# Backend for Twilio Services

This repository contains the backend service for a project that integrates with Twilio to provide voice calls, SMS messaging, and OTP verification.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

* Node.js
* npm

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```
2. Install the dependencies:
   ```bash
   npm install
   ```

### Configuration

Create a `.env` file in the root of the project and add the following environment variables:

```
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=your_twilio_phone_number
TWILIO_VERIFY_SID=your_twilio_verify_sid
```

You can find these values in your Twilio console.

## Usage

To start the server, run the following command:

```bash
npm start
```

The server will start on port 5000.

## API Documentation

### Make a Voice Call

* **POST** `/api/twilio-call`

Initiates a voice call to a specified phone number.

**Request Body:**

* `to` (string, required): The phone number to call.
* `message` (string, required): The message to be spoken.

**Example:**

```bash
curl -X POST http://localhost:5000/api/twilio-call \
     -H "Content-Type: application/json" \
     -d '{"to": "+1234567890", "message": "Hello from Twilio!"}'
```

### Send an SMS Message

* **POST** `/api/twilio-message`

Sends an SMS message to a specified phone number.

**Request Body:**

* `to` (string, required): The phone number to send the message to.
* `messageText` (string, required): The text of the message.

**Example:**

```bash
curl -X POST http://localhost:5000/api/twilio-message \
     -H "Content-Type: application/json" \
     -d '{"to": "+1234567890", "messageText": "Hello from Twilio!"}'
```

### Send an OTP

* **POST** `/api/twilio-send-otp`

Sends a one-time password (OTP) to a specified phone number.

**Request Body:**

* `phone` (string, required): The phone number to send the OTP to.

**Example:**

```bash
curl -X POST http://localhost:5000/api/twilio-send-otp \
     -H "Content-Type: application/json" \
     -d '{"phone": "+1234567890"}'
```

### Verify an OTP

* **POST** `/api/twilio-verify-otp`

Verifies a one-time password (OTP) for a specified phone number.

**Request Body:**

* `phone` (string, required): The phone number the OTP was sent to.
* `otp` (string, required): The OTP to verify.

**Example:**

```bash
curl -X POST http://localhost:5000/api/twilio-verify-otp \
     -H "Content-Type: application/json" \
     -d '{"phone": "+1234567890", "otp": "123456"}'
```
