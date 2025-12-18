# Standardized Troubleshooting Recipe for Azure-Hosted ASP.NET Core Applications


## 1. **Establish the Baseline** 

### Read issue description/talk to customer
 - Do we have a clear understanding of the issue?
 - Where does it happen? AdminApp or Portal?
 - Is it a general or a tenant specific problem?

### Check Application Availability
- Navigate to Azure Portal → App Service → Overview
- Verify __Status__ shows "Running"
- Review __Restart count__ for recent restarts

### Information from browser
1. Try to reproduce the issue the customer has. Do we get the same outcome.
2. Check javascript console for errors and logging messages.
3. Look at the network tab. Are there slow requests.

### Verify Recent Deployments
- Check __Deployment Center__ → Logs
- Confirm last deployment timestamp and status
- Compare timing with reported issue onset

## 2. **Examine Monitoring Data**

### Failed Requests
1. Navigate to Application Insights → __Failures__
2. Filter by time range matching the incident
3. Look for HTTP status codes: `500`, `502`, `503`, `504`
4. Click into individual failures to see:
   - Full exception stack traces
   - Request properties (headers, query strings)
   - Custom telemetry events

### Performance Issues
1. Application Insights → __Performance__
2. Check:
   - Slowest operations (look for >5s response times)
   - Dependency calls (Cosmos DB, Azure Search, SQL Server, Blob Storage)
   - Database query performance

### Custom Logging
```csharp
// Your functions use ILogger - search for these in Application Insights
_logger.LogError(...)
_logger.LogWarning(...)
```
- Application Insights → __Logs__ (Kusto Query)
- Use query:
```kql
traces
| where timestamp > ago(1h)
| where severityLevel >= 3
| order by timestamp desc
```

## 3. **Review App Service Diagnostics**

### Live Metrics Stream
- Application Insights → __Live Metrics__
- Real-time view of:
  - Incoming request rate
  - Failed request count
  - Memory and CPU usage
  - Active exceptions

### App Service Logs
- App Service → __Monitoring__ → __Log stream__
- Shows real-time stdout/stderr
- Look for:
  - Startup errors
  - Configuration issues
  - Authentication failures

### Diagnostic Tools
- App Service → __Diagnose and solve problems__
- Run automated diagnostics:
  - "Application Crashes"
  - "Slow Performance"
  - "High Memory Usage"

## 4. **Investigate Dependencies**

Your app has multiple Azure service dependencies:

### Cosmos DB
- Check metrics: __Request Units__, __Throttled Requests (429s)__
- Review __Data Explorer__ for data integrity
- Verify connection string in __Configuration__

### Azure SQL Database
- Check __DTU/vCore usage__
- Review __Query Performance Insight__
- Check for blocking queries

### Azure AI Search
- Verify index health: __Search Explorer__
- Check indexer status and errors
- Review throttling metrics

### Azure Storage (Blobs)
- Check __Metrics__ for throttling
- Verify SAS token validity (if used)

### External APIs
- Check __Application Insights → Dependencies__
- Filter by dependency type: HTTP
- Look for timeouts or failures to external endpoints

## 5. **Configuration & Authentication Issues**

### App Configuration

1. App Service → __Configuration__ → __Application settings__
2. Verify critical settings exist:
   - `CosmosConnection`
   - Connection strings for SQL Server
   - Azure Search endpoint and keys
   - Azure OpenAI configuration
3. Check __App Configuration__ service in Azure Portal
4. Verify managed identity permissions if using Key Vault references

### Authentication Problems
Your app uses multiple auth methods (JWT, SAML2, Identity):

- Check __Authentication__ blade
- Review Application Insights for 401/403 errors
- Verify certificate validity: `SPITZEX509.pfx`
- Check __Microsoft Entra ID__ (Azure AD) app registration

## 6. **Resource Constraints**

### Scaling Issues
- App Service → __Scale up (App Service plan)__
- Check current tier and resource allocation
- Review __Metrics__:
  - CPU percentage (>80% sustained = issue)
  - Memory percentage (>85% = potential problem)
  - HTTP queue length (>10 = backlog)

### Auto-scaling
- Check __Scale out (App Service plan)__
- Verify auto-scale rules are triggering correctly

## 7. **Check for Known Issues**

### Azure Service Health
- Azure Portal → __Service Health__
- Check for active incidents in your region
- Review planned maintenance

### Package Vulnerabilities
Your app uses many NuGet packages - check for:
- Security vulnerabilities in dependencies
- Known bugs in specific package versions

## 8. **Reproduce and Debug Locally** (If needed)

### Pull Configuration
```sh
# Download app settings
az webapp config appsettings list --name <app-name> --resource-group <rg-name>
```

## 9. **Fix and Verify**

### Deploy Fix
1. Make code changes locally
2. Test thoroughly on local machine
3. Deploy via your deployment pipeline to test environment
4. Test app in test environment and review code with peers

### Post-Fix Verification
- Monitor __Live Metrics__ for 15-30 minutes
- Check error rates return to baseline
- Verify performance metrics stabilize

## Priority Order Template

**For errors/crashes:**
```
Application Insights Failures → App Service Logs → Dependency Health → Configuration
```

**For performance issues:**
```
Application Insights Performance → Live Metrics → Dependency Metrics → Resource Constraints → Database Performance
```

**For intermittent issues:**
```
Live Metrics (wait for occurrence) → Correlation in Application Insights → Dependency timing → Auto-scaling events
```

## Key Telemetry Queries

Save these in Application Insights __Workbooks__:

```kql
// All errors in last hour
exceptions
| where timestamp > ago(1h)
| summarize count() by type, outerMessage
| order by count_ desc

// Slow requests
requests
| where timestamp > ago(1h)
| where duration > 5000
| project timestamp, name, duration, resultCode, operation_Id
| order by duration desc

// Dependency failures
dependencies
| where timestamp > ago(1h)
| where success == false
| summarize count() by name, resultCode
```

This systematic approach ensures you examine the most likely problem areas first while avoiding information overload from Azure's extensive telemetry.