# Introduction
 
The official base link for all requests is
```
https://xincraft.net/api/v{version}/
```
Example
```
https://xincraft.net/api/v1/player/username/RaymondDev
```


### API Versions

| Version | Status                           | Default |
|---------|----------------------------------|---------|
| 1       | Available                        | ✓       |
| dev     | Not Public                       |         |
Replace `{version}` with any version above.

### Authentication

Each request must have a `xincraft-api` header. This will authenticate your requests, and requires an API key.

#### Acquiring an API key

Join our [discord](https://discord.gg/xincraft), and use the slash command `/api`. Follow the steps to create a new key.

#### Example Authentication Header
```
xincraft-api: 1234567890
```


### Error Messages

When a request to the API fails, you receive a `"success": boolean` and `"cause": string`. You can use these fields to debug and find out what went wrong. If the request returns `"success": true`, that means the request was successful. All failed requests return `"success": false`.

#### Example
```json
{
  "success": false,
  "cause": "Invalid API key provided!" 
}
```

### Rate Limiting

The HTTP API implements a process for limiting and preventing excessive requests. API users that regularly hit and ignore rate limits will have their API keys revoked, and be blocked from using the API further.