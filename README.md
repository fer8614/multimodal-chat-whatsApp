# Multimodal Chat WhatsApp

Intelligent WhatsApp chatbot with artificial intelligence using n8n. This workflow implements an advanced AI-powered chatbot to manage automatic conversations on WhatsApp with multimodal capabilities.

## 📋 Description

This n8n workflow automates WhatsApp conversations with:

- **AI Agent**: Automatically responds to messages using OpenAI's GPT-4
- **Audio Processing**: Transcribes voice messages to text
- **Image Analysis**: Analyzes and describes images sent by users
- **Conversation Memory**: Maintains context from previous conversations using PostgreSQL
- **Intelligent Routing**: Directs messages based on their type (text, audio, image)
- **Database Integration**: Access to customer and product database for intelligent recommendations
- **Calculator Tool**: Performs calculations when needed

## 🚀 Features

- ✅ Automatic responses with AI (GPT-4)
- ✅ Voice message transcription to text
- ✅ Image analysis and description
- ✅ Conversation context management
- ✅ Integration with WhatsApp Business API
- ✅ Integration with OpenAI for language processing
- ✅ PostgreSQL memory storage
- ✅ Multimodal message handling (text, audio, images)
- ✅ Google Sheets database integration
- ✅ Calculator tool for computations

## 📦 Requirements

- n8n account
- WhatsApp Business API access
- OpenAI API credentials
- PostgreSQL database (for conversation memory)
- Google Sheets API credentials (for database functionality)

## 🔧 Installation

1. Access your n8n instance
2. Import the `workflow.json` file
3. Configure the necessary credentials:
   - WhatsApp Business API credentials
   - OpenAI API Key
   - PostgreSQL connection string
   - Google Sheets API credentials

## 📝 Configuration

### Environment Variables

```bash
WHATSAPP_API_TOKEN=your_token_here
WHATSAPP_PHONE_NUMBER_ID=your_phone_id
OPENAI_API_KEY=your_key_here
POSTGRES_CONNECTION_STRING=postgresql://user:password@host:port/database
GOOGLE_SHEETS_API_KEY=your_api_key
```

### Main Nodes

- **Webhook1**: Receives messages from WhatsApp
- **Filtrardor**: Filters and validates incoming messages
- **Switch**: Routes based on message type (text, audio, image)
- **Transcribir Audio**: Converts voice messages to text
- **Explicar Imagen**: Analyzes images using GPT-4 Vision
- **Agente de IA**: AI agent that processes and responds to messages
- **Postgres Chat Memory**: Stores conversation history
- **Base de Datos**: Google Sheets database for customer/product info
- **Calculadora**: Calculator tool for computations
- **Enviar Mensaje**: Sends responses back to WhatsApp

## 🎯 Use Cases

- **Course Sales**: Automated customer service for online course sales
- **Customer Support**: Automatic support with context awareness
- **Sales Assistant**: Product recommendations and inquiries
- **Information Bot**: Answer questions with image and audio support
- **Lead Generation**: Collect customer data and schedule appointments

## 🔐 Security Notes

- Never commit API keys or tokens to version control
- Use n8n's credential management system
- Store sensitive data in environment variables
- Ensure PostgreSQL connection is secure
- Validate all incoming WhatsApp messages

## 📞 Support

For more information about n8n, visit: https://n8n.io/docs/

For WhatsApp Business API documentation: https://developers.facebook.com/docs/whatsapp/

For OpenAI documentation: https://platform.openai.com/docs/

## 📄 License

This project is available under an open license.

## 👤 Author

Created by: Yesid Fernando Cepeda B.

---

**Last updated**: 2026-01-16
