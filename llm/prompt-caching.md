# Prompt Caching

Prompt caching can improve cost and latency for API calls to the model. Prompt caching works the following way: When structuring a prompt it is important to have the static content in the beginning of the prompt and specific
information at the end. This way the prefix of the prompt will be the same and thus we can make use of caching. On each request, the API will make a lookup on the cache key to find the machine with the cached prompt. If
prefix of the prompt is not found in the cache keys, the system will process the complete prompt. This will result in higher latency and higher costs. 
