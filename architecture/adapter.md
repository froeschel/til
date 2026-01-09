# Adapter Pattern

## Purpose
The Adapter pattern converts the interface of a class into another interface that clients expect. It acts as a bridge between incompatible interfaces, allowing classes with incompatible contracts to work together without modifying their source code.

## When to Use
Use the Adapter pattern when:
- You need to integrate a third-party library with an incompatible interface
- You want to use legacy code alongside new code with different interfaces
- You need to provide a consistent interface to multiple implementations with different contracts
- You're wrapping external services (APIs, databases, etc.) with different signatures

## Structure
The pattern typically involves:
1. **Target Interface**: The interface the client expects
2. **Adaptee**: The existing interface that needs to be adapted (incompatible)
3. **Adapter**: Implements the target interface and translates calls to the adaptee

## Real-World Example: Weather Service Adapters

Imagine you're building a weather application that needs to support multiple weather data providers. Each provider has a different interface:

```csharp
// Target Interface - what our application expects
public interface IWeatherService
{
    double GetTemperatureForCity(string city);
}

// Adaptee interfaces - incompatible external APIs
public interface ISourceWeatherServiceOne 
{
    double GetTemperatureForLocation(string city);
}

public interface ISourceWeatherServiceTwo
{
    string GetTemperatureForArea(string city);
}

// Concrete implementations of external services
public class SourceWeatherServiceOne : ISourceWeatherServiceOne
{
    public double GetTemperatureForLocation(string city)
    {
        return 1.5;
    }
}

public class SourceWeatherServiceTwo : ISourceWeatherServiceTwo
{
    public string GetTemperatureForArea(string city)
    {
        return "10";
    }
}

// Adapters - convert external interfaces to our target interface
public class WeatherServiceOneAdapter : IWeatherService
{
    private readonly ISourceWeatherServiceOne _sourceWeatherServiceOne;

    public WeatherServiceOneAdapter(ISourceWeatherServiceOne sourceWeatherServiceOne)
    {
        _sourceWeatherServiceOne = sourceWeatherServiceOne;
    }

    public double GetTemperatureForCity(string city)
    {
        // Simple delegation - method names align
        return _sourceWeatherServiceOne.GetTemperatureForLocation(city);
    }
}

public class WeatherServiceTwoAdapter : IWeatherService
{
    private readonly ISourceWeatherServiceTwo _sourceWeatherServiceTwo;

    public WeatherServiceTwoAdapter(ISourceWeatherServiceTwo sourceWeatherServiceTwo)
    {
        _sourceWeatherServiceTwo = sourceWeatherServiceTwo;
    }

    public double GetTemperatureForCity(string city)
    {
        // Translate interface: convert string return to double
        return double.Parse(_sourceWeatherServiceTwo.GetTemperatureForArea(city));
    }
}