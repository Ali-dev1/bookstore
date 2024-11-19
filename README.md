# BookMarket

A modern e-commerce platform for books with M-Pesa integration, built with Vue.js.

## Features

- 📚 Browse and search books
- 🛒 Shopping cart functionality
- 💳 M-Pesa payment integration
- 🇰🇪 Localized for the Kenyan market
- 📱 Responsive design

## Tech Stack

- Vue.js 3
- Tailwind CSS
- Axios for API calls
- Vue Toastification for notifications

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the development server:
   ```bash
   npm run dev
   ```

## M-Pesa Integration

The application integrates with M-Pesa's Daraja API for payments. To test payments:

1. Use a Safaricom number in the format `7XXXXXXXX`
2. The sandbox environment is configured for testing
3. Payment status updates are shown in real-time

## Environment Setup

Before running the application, make sure to configure your M-Pesa API credentials in `src/services/mpesa.js`:

- CONSUMER_KEY
- CONSUMER_SECRET
- BUSINESS_SHORT_CODE
- PASS_KEY

## Project Structure

```
src/
├── assets/         # Static assets
├── components/     # Vue components
├── services/       # API services
└── style.css      # Global styles
```
