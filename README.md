# QUICKLIFT

A full-stack QUICKLIFT Application built with React Native and Expo.

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (v16 or higher)
- npm or yarn
- Expo CLI
- Git
- A code editor (VS Code recommended)

## Required Accounts and API Keys

1. **Clerk Authentication**
   - Sign up at [clerk.com](https://clerk.com)
   - Create a new application
   - Get your API keys (PUBLISHABLE_KEY and SECRET_KEY)

2. **Stripe Payment**
   - Sign up at [stripe.com](https://stripe.com)
   - Get your API keys (PUBLISHABLE_KEY and SECRET_KEY)

3. **NeonDB (PostgreSQL)**
   - Sign up at [neon.tech](https://neon.tech)
   - Create a new project
   - Get your database connection string

4. **Google Maps API**
   - Go to [Google Cloud Console](https://console.cloud.google.com)
   - Create a new project
   - Enable Maps SDK
   - Get your API key

## Environment Setup

1. Create a `.env` file in the root directory with the following variables:
```env
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
EXPO_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
STRIPE_SECRET_KEY=your_stripe_secret_key
DATABASE_URL=your_neon_db_connection_string
EXPO_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_api_key
```

## Installation Steps

1. **Clone the repository**
```bash
](https://github.com/anilrana004/QUICKLIFT.git)
cd QUICKLIFT
```

2. **Install dependencies**
```bash
npm install
```

3. **Database Setup**
   - Connect to your NeonDB database
   - Run the database migrations (if any)
   - Set up the required tables

4. **Start the development server**
```bash
# For mobile development
npx expo start

# For web development
npx expo start --web
```

## Project Structure

```
Uber-Clone/
├── app/                    # Main application code
│   ├── (api)/             # API routes
│   ├── (auth)/            # Authentication screens
│   └── (root)/            # Main app screens
├── components/            # Reusable components
├── assets/               # Images, icons, and fonts
├── constants/            # Constants and configuration
├── lib/                  # Utility functions
├── store/               # State management
└── types/               # TypeScript definitions
```

## Key Features Implementation

1. **Authentication**
   - Sign up/Sign in with Clerk
   - Social authentication (Google)
   - User profile management

2. **Map Integration**
   - Real-time location tracking
   - Route visualization
   - Driver location updates

3. **Ride Booking**
   - Location selection
   - Driver matching
   - Fare calculation
   - Ride status tracking

4. **Payment System**
   - Stripe integration
   - Payment processing
   - Transaction history

5. **Chat System**
   - Real-time messaging
   - Driver-passenger communication

## Common Issues and Solutions

1. **Environment Variables**
   - Ensure all environment variables are properly set
   - Check for any missing API keys

2. **Database Connection**
   - Verify database connection string
   - Check database permissions

3. **Map Loading**
   - Verify Google Maps API key
   - Check API key restrictions

4. **Payment Processing**
   - Ensure Stripe keys are correct
   - Test with Stripe test cards

## Testing

1. **Mobile Testing**
   - Install Expo Go app on your device
   - Scan QR code from terminal
   - Test on both iOS and Android

2. **Web Testing**
   - Open in Chrome
   - Test responsive design
   - Check all features

## Deployment

1. **Frontend Deployment**
   - Build the app: `expo build:web`
   - Deploy to hosting service (Vercel, Netlify)

2. **Backend Deployment**
   - Deploy API routes to serverless platform
   - Set up database backups
   - Configure environment variables

## Author

Anil Rana

## License

MIT 
