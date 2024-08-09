# YouTube Transcript API

This project is a Cloudflare Worker that provides an API for retrieving transcripts from YouTube videos. It allows users to fetch transcript data in JSON, SRT, or plain text format.

## Features

- Fetch transcripts from YouTube videos using the video URL
- Support for multiple output formats: JSON, SRT, and plain text
- OpenAPI specification for easy integration
- Error handling for invalid URLs, missing transcripts, and more

## API Usage

### Endpoint

`GET /api/transcript`

### Parameters

- `url` (required): The full URL of the YouTube video
- `output` (optional): The desired output format (json, srt, or text). Defaults to json.

### Example Request

```
https://your-worker-url.workers.dev/api/transcript?url=https://www.youtube.com/watch?v=dQw4w9WgXcQ&output=json
```

### Response Formats

1. JSON (default):
   ```json
   [
     {
       "text": "Never gonna give you up",
       "start": 0.5,
       "duration": 2.3
     },
     ...
   ]
   ```

2. SRT:
   ```
   1
   00:00:00,500 --> 00:00:02,800
   Never gonna give you up

   2
   00:00:02,800 --> 00:00:05,100
   Never gonna let you down
   ```

3. Plain Text:
   ```
   Never gonna give you up
   Never gonna let you down
   ...
   ```

## OpenAPI Specification

The API provides an OpenAPI specification at the `/openapi.json` endpoint. This can be used to generate client libraries or integrate with API documentation tools.

## Error Handling

The API returns appropriate HTTP status codes and error messages for various scenarios:

- 400: Bad request (Invalid YouTube URL or output format)
- 404: Transcript not available for the video
- 429: Rate limit exceeded
- 500: Internal server error

## Development
This project is designed to run on Cloudflare Workers. To set up the development environment:

1. Install Wrangler:
`npm install -g wrangler`

2. Authenticate Wrangler with your Cloudflare account:
`wrangler login`
Follow the prompts to log in through your browser.

3. Clone this repository:
`git clone https://github.com/jamesflores/youtube-subtitles-worker.git`
cd youtube-subtitles-worker

4. Configure your wrangler.toml file with your account details and Worker name.

5. Run the development server:
`wrangler dev`
This will start a local server for testing your Worker.

6. To deploy to Cloudflare Workers:
`wrangler deploy`

## License

MIT License

## Contributing

Submit a pull request 

## Support

james [at] jamesflores [dot] net