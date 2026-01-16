# Setup Guide - Multimodal Chat WhatsApp

## Step 1: Prepare Credentials

### WhatsApp Business API
1. Go to https://developers.facebook.com/
2. Create a Meta Business Account if you don't have one
3. Create a WhatsApp Business App
4. Get your:
   - Phone Number ID
   - Access Token
   - Business Account ID

### OpenAI API
1. Go to https://platform.openai.com/api-keys
2. Create a new API key
3. Copy the key (you'll need it in n8n)

### PostgreSQL (Recommended)
For conversation memory and context:
1. Set up a PostgreSQL database
2. Create a table named `conversaciones` with the following structure:
```sql
CREATE TABLE conversaciones (
  id SERIAL PRIMARY KEY,
  session_id VARCHAR(255),
  message TEXT,
  response TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
3. Get your connection string: `postgresql://user:password@host:port/database`

### Google Sheets (For Database)
If you want to use Google Sheets as a database:
1. Create a Google Sheet with your customer/product data
2. Enable Google Sheets API in Google Cloud Console
3. Create OAuth 2.0 credentials
4. Get your Sheet ID from the URL

## Step 2: Import Workflow in n8n

1. Open your n8n instance
2. Go to "Workflows" → "Import"
3. Upload the `workflow.json` file
4. Click "Import"

## Step 3: Configure Credentials in n8n

### WhatsApp Business API Credentials
1. Find the "Webhook1" node
2. Click on it and go to the credentials section
3. Select "Create New" → "WhatsApp Business Cloud API"
4. Enter your credentials:
   - Phone Number ID
   - Access Token
   - Business Account ID
5. Save

### OpenAI Credentials
1. Find nodes that use OpenAI (Transcribir Audio, Agente de IA, etc.)
2. For each node:
   - Click on the node
   - Go to credentials section
   - Select "Create New" → "OpenAI"
   - Paste your API key
   - Save

### PostgreSQL Credentials
1. Find the "Postgres Chat Memory" node
2. Click on it
3. Go to credentials section
4. Select "Create New" → "PostgreSQL"
5. Enter your connection details:
   - Host
   - Port (default: 5432)
   - Database name
   - Username
   - Password
6. Save

### Google Sheets Credentials
1. Find the "Base de Datos" node
2. Click on it
3. Go to credentials section
4. Select "Create New" → "Google Sheets"
5. Follow OAuth authentication
6. Select your spreadsheet
7. Save

## Step 4: Configure WhatsApp Webhook

1. In the "Webhook1" node, copy the webhook URL
2. Go to your WhatsApp Business App settings
3. Set the webhook URL to the one from n8n
4. Verify the webhook token
5. Subscribe to message events

## Step 5: Test the Workflow

1. Activate the workflow (toggle "Active" in the top right)
2. Send a message to your WhatsApp Business number
3. Check if you receive an automatic response
4. Review the "Executions" tab for any errors

## Step 6: Customize AI Behavior

### Modify the AI Agent Prompt

1. Open the "Agente de IA" node
2. Edit the "System Message" field
3. Customize the AI's behavior, tone, and instructions
4. Save changes

### Example: Change from Course Sales to Customer Support

Replace the system message with:
```
You are a customer support assistant for WhatsApp. Your role is to:
1. Answer customer questions professionally
2. Help resolve issues
3. Provide product information
4. Escalate complex issues when needed

Always be polite, helpful, and maintain conversation context.
```

## Troubleshooting

### Webhook Not Receiving Messages
- Verify the webhook URL is correct in WhatsApp settings
- Check that the workflow is active
- Review WhatsApp Business API logs
- Ensure n8n is accessible from the internet

### No AI Responses
- Verify OpenAI API key is valid
- Check that you have available credits
- Review execution logs for errors
- Ensure the system message is properly configured

### Audio Transcription Fails
- Verify the audio file format is supported
- Check OpenAI API quota
- Ensure the audio is clear and not too long
- Review error messages in executions

### Image Analysis Not Working
- Verify the image format is supported (JPG, PNG, etc.)
- Check image size (should be reasonable)
- Ensure OpenAI API supports vision models
- Review error messages in executions

### PostgreSQL Connection Issues
- Verify connection string is correct
- Check database is running and accessible
- Ensure firewall allows connection
- Verify table exists with correct schema

### Google Sheets Not Updating
- Verify Google Sheets credentials are valid
- Check that the sheet ID is correct
- Ensure the sheet is shared with the service account
- Review error messages in executions

## Advanced Configuration

### Add Custom Tools

You can add more tools to the AI agent by:
1. Adding new nodes (e.g., database queries, API calls)
2. Connecting them as tools to the "Agente de IA" node
3. Updating the system message to explain the new tools

### Enable Logging

For debugging:
1. Add a "Log" node after key steps
2. Configure what data to log
3. Review logs in the "Executions" tab

### Rate Limiting

To prevent abuse:
1. Add a "Rate Limit" node after the trigger
2. Configure limits per user/chat
3. Handle exceeded limits appropriately

### Message Filtering

To filter certain types of messages:
1. Modify the "Filtrardor" node conditions
2. Add additional validation rules
3. Route unwanted messages appropriately

## Resources

- [n8n Documentation](https://n8n.io/docs/)
- [WhatsApp Business API](https://developers.facebook.com/docs/whatsapp/)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Google Sheets API](https://developers.google.com/sheets/api)

---

Need help? Check the workflow execution logs for detailed error messages.
