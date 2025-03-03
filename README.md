# ✈️ FlightAI: AI-Powered Virtual Airline Assistant

![image](https://github.com/user-attachments/assets/7916ad7b-12a1-4227-aa30-9dd7b4104586)

## 🏗️ System Architecture
FlightAI is a sophisticated virtual assistant for a premium airline, designed to provide customers with accurate and helpful information about flights, bookings, and travel services. The system integrates a conversational AI interface with a mock airline database to simulate real-world interactions between customers and an airline's digital assistant.

### 🔧 Core Components
- **Conversational AI Engine**: Utilizes the Ollama API with a Llama 3.2 model for natural language understanding and generation.
- **Mock Airline Database**: A Python class simulating an airline's backend systems.
- **Tool Functions**: A set of functions allowing AI to query the database.
- **Gradio Web Interface**: A modern, responsive UI for customer interactions.

## ✨ Key Features

### 1️⃣ Flight Information Services 🛫
- **Flight Search**: Find flights between origin and destination cities with date filtering.
- **Ticket Pricing**: Get pricing details based on class type and booking date.
- **Flight Status**: Check if flights are on time, delayed, or boarding.

### 2️⃣ Customer Profile Management 👤
- **User Profiles**: Load customer profiles via email for personalized responses.
- **Loyalty Program Integration**: Access loyalty status, points, and tier benefits.
- **Preference Management**: Store seat, meal, and travel preferences.

### 3️⃣ Travel Information 🌍
- **Destination Guides**: Get details about destinations, airport codes, and attractions.
- **Baggage Allowance Calculator**: Determine baggage limits based on loyalty tier and class.
- **Travel Documentation**: Provide information on travel requirements and policies.

### 4️⃣ Conversational Interface 🗣️
- **Context Awareness**: Maintains conversation history for relevant responses.
- **Tool Integration**: Connects AI responses with database queries.
- **Professional Tone**: Ensures a friendly, premium airline brand experience.

## 🖥️ Technical Implementation

### ⚙️ AI Model Configuration
The system uses a locally hosted Llama 3.2 model via Ollama:
```python
MODEL = "llama3.2"
client = OpenAI(base_url='http://localhost:11434/v1', api_key='ollama')
```
The AI assistant is guided by a system message defining its role:
```python
system_message = """
You are FlightAI, a professional and helpful virtual assistant for a premium airline.
Your goal is to provide accurate, helpful, and courteous responses to customer inquiries.
Keep responses concise but complete - generally no more than 3 sentences unless more detail is required.
If you don't know an answer, acknowledge this and offer to connect the customer with a human agent.
Use a friendly, professional tone that represents the premium brand image of the airline.
"""
```

### 🗄️ Database Structure
The `FlightDatabase` class simulates airline systems:
- **Flight Data**: Details about flights (origins, destinations, schedules, prices, available seats).
- **Flight Status**: Real-time flight updates.
- **Destinations**: City details including prices, airport codes, attractions.
- **Loyalty Program**: Tier structures, benefits, and point requirements.
- **User Profiles**: Customer information including loyalty status and preferences.

### 🔧 Tool Functions
AI accesses the database via specialized functions:
```python
 tools = [
    {
        "type": "function",
        "function": {
            "name": "get_ticket_price",
            "description": "Get the price of a ticket to the destination city",
            "parameters": { ... }
        }
    },
    # Other tool definitions...
]
```
#### 📜 Available Functions:
- `get_ticket_price`: Retrieves ticket pricing.
- `search_flights`: Finds flights matching criteria.
- `get_flight_status`: Checks flight status.
- `get_destination_info`: Fetches city details.
- `get_user_info`: Accesses user profiles.
- `check_baggage_allowance`: Calculates baggage limits.

## 🔄 Conversation Flow
1️⃣ **User Input** → User submits a query via Gradio.
2️⃣ **Message Processing** → The message is added to conversation history.
3️⃣ **AI Response Generation** → The system queries the AI model.
4️⃣ **Tool Execution** → AI calls tools if needed.
5️⃣ **Final Response** → AI composes the response.
6️⃣ **UI Update** → Response is displayed to the user.

Example:
```plaintext
User: "How much is a ticket to London?"
AI → System: Calls `get_ticket_price("london")`
Database → System: Returns ticket price
System → AI: AI integrates price into response
AI → User: "A ticket to London (LHR) costs $799 for economy class. Business class starts at $1,997.50, first class at $3,196."
```

## 🎨 User Interface (UI)
The Gradio interface features:
- **💬 Chat Panel**: Main interaction window.
- **👤 User Profile Panel**: Personalized assistance options.
- **✈️ Flight Search Panel**: Browse available flights.
- **🔗 Quick Links**: Access common information pages.

💠 *Custom dark theme with blue and teal accents for a premium feel.*

## 📁 Data Structures
### ✈️ Flight Data Format
```python
{
    "LON123": {
        "origin": "New York",
        "destination": "London",
        "departure": "2025-03-10 08:30",
        "arrival": "2025-03-10 20:45",
        "price": 799,
        "available_seats": 42
    }
}
```

### 👤 User Profile Format
```python
{
    "john.doe@example.com": {
        "name": "John Doe",
        "loyalty_tier": "Gold",
        "loyalty_points": 28540,
        "upcoming_flights": ["LON123"],
        "preferences": {"seat": "window", "meal": "vegetarian"}
    }
}
```

## 🔍 Implementation Considerations
### ⚠️ Error Handling
- API failures 🚫
- Invalid/missing data ⚠️
- User not found scenarios ❌

### 🚀 Performance Optimization
- Efficient data structures 📊
- Minimized AI API calls ⏳
- Logging for debugging 📝

### 🔒 Security Considerations
- Secure authentication 🔑
- Data encryption 🔐
- API rate limiting 🚦
- Input validation ✅

## 🔮 Future Enhancements
✅ **Real Database Integration**: Connect to actual airline reservation systems.
✅ **Multi-language Support**: Expand accessibility.
✅ **Booking Functionality**: Enable users to book flights.
✅ **Payment Processing**: Integrate secure transactions.
✅ **Web/Mobile App Integration**: Extend to airline's apps.
✅ **Voice Interface**: Add speech recognition.

## 🎯 Conclusion
FlightAI is a cutting-edge AI assistant for premium airlines, combining NLP with domain-specific knowledge and a user-friendly interface. Its modular architecture allows easy expansion and real-world airline integration.

✈️ **Enhancing airline customer service through AI!**
