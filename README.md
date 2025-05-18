# Weather API with Google ADK

A Python-based weather information system that uses Google's Agent Development Kit (ADK) to create an intelligent weather assistant. The system fetches real-time weather data for Indian cities using the WeatherAPI.com service.

## Features

- Real-time weather data for Indian cities
- Interactive conversation interface
- Secure API key management
- Detailed weather information including:
  - Temperature
  - Weather condition
  - Humidity
  - Wind speed
  - Location details
  - Last updated timestamp

## Prerequisites

- Python 3.x
- Google ADK
- WeatherAPI.com account
- Google AI Studio account (for Gemini API)

## Installation

1. Install the required packages:
```bash
pip install google-adk
pip install httpx
```

2. Set up your API keys:
   - Get your WeatherAPI.com key from [WeatherAPI.com](https://www.weatherapi.com/)
   - Get your Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey)

## Configuration

The system requires two API keys:
1. `GEMINI_API_KEY`: For Google's Gemini model
2. `WEATHER_API_KEY`: For WeatherAPI.com service

Store these keys securely using your preferred method (e.g., environment variables, secure key management system).

## Code Structure

### 1. Weather Tool (`get_weather`)
```python
def get_weather(city: str) -> str:
    """Fetches current weather data for a city in India."""
```
- Takes a city name as input
- Returns formatted weather information
- Handles API errors gracefully
- Focuses on Indian cities

### 2. Weather Agent
```python
weather_agent = Agent(
    name="weather_agent_v1",
    model="gemini-2.0-flash",
    description="Provides weather information for specific cities.",
    instruction="You are a helpful weather assistant...",
    tools=[get_weather]
)
```
- Uses Gemini 2.0 Flash model
- Configured to handle weather queries
- Includes clear instructions for the AI

### 3. Session Management
```python
session_service = InMemorySessionService()
```
- Manages conversation history
- Maintains session state
- Uses in-memory storage for simplicity

### 4. Interactive Interface
```python
async def run_interactive_conversation():
    # Interactive conversation loop
```
- Provides a command-line interface
- Supports continuous conversation
- Allows easy exit with 'exit' command

## Usage

1. Start the interactive conversation:
```python
await run_interactive_conversation()
```

2. Ask weather-related questions:
```
Ask me something (or type 'exit' to quit): What's the weather in Mumbai?
```

3. The system will respond with detailed weather information:
```
Location: Mumbai, Maharashtra, India
Temperature: 28°C
Condition: Partly cloudy
Humidity: 75%
Wind Speed: 12 km/h
Last Updated: 2024-03-21 15:30
```

## Error Handling

The system includes robust error handling:
- API connection timeouts (30 seconds)
- Invalid city names
- API response errors
- Network issues

## Security Considerations

- API keys are stored securely
- HTTPS is used for API calls
- Input validation for city names
- Error messages don't expose sensitive information

## Limitations

- Currently limited to Indian cities
- Requires active internet connection
- Weather data depends on WeatherAPI.com availability
- In-memory session storage (not persistent)

## Future Improvements

Potential enhancements could include:
- Support for international cities
- Weather forecasts
- Historical weather data
- Persistent session storage
- Web interface
- Multiple language support

## Contributing

Feel free to submit issues and enhancement requests!

## License

[Add your preferred license here] 