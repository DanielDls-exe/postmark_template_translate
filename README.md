# Postmark Template Translate

A library to send Postmark templates with translated content.

## Installation

To install the library, use pip:

```bash
pip install postmark-template-translate
```

## Usage

### Configuration

First, configure the PostmarkService with your Postmark server token:

```python
from postmark_template_translate.postmark import config

# Configure the service with your Postmark server token
postmark_service = config.configure(server_token='your-postmark-server-token')
```
### Sending Translated Emails

Use the send_translated_email method to send emails with translated content. Below is an example of how to use this method.

### Example

```python
from postmark_template_translate.postmark import config

# Step 1: Configure the Postmark service
postmark_service = config.configure(server_token='xxxxxxxxxxxxxxxxxx')

# Replace 'xxxxxxxxxxxxxxxxxx' with your actual Postmark server token.

# Step 2: Define the model with the template variables
model = {
    "fullName": "Daniel Alvarado",
    "email": "danieldls.ucv@gmail.com",
    "phoneNumber": "1234567890",
    "arrivalDate": "2024-01-01",
    "departureDate": "2024-01-10",
    "villaType": "Morna",
    "observations": "No special requests"
}

# Step 3: Specify the template ID
template_id = '12345678'


# Step 4: Define additional email parameters
language = 'pt'  # Target language code
from_email = 'xxxxx@xxxx.com'
to_email = 'xxxxx@xxxx.com'
message_stream = 'outbound'

# - 'from_email': The email address that you have registered and signed in Postmark.
# - 'to_email': The recipient's email address.
# - 'language': The target language code to which the template should be translated. For example, 'pt' for Portuguese.
# - 'message_stream': The message stream to use in Postmark. Replace 'outbound' with your actual message stream if different.

# Step 5: Send the translated email
postmark_service.send_translated_email(
    template_id=template_id,
    model=model,
    language=language,
    from_email=from_email,
    to_email=to_email,
    message_stream=message_stream
)
```