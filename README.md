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

## Deployment and Hosting

This section provides guidance on deploying and hosting your QUICKLIFT application, covering mobile app distribution, web version deployment, and backend services.

### Understanding 'Hosting' for This Project

For mobile applications targeting iOS and Android, "hosting" is fundamentally about **distribution**. The compiled app (e.g., `.ipa` for iOS, `.aab` or `.apk` for Android) is submitted to the Apple App Store and Google Play Store, which handle delivery to users.

Expo also allows building a web version of your application. This web build results in static files (HTML, CSS, JavaScript) that can be deployed to any **static web hosting service** (e.g., Vercel, Netlify, AWS S3, GitHub Pages, Firebase Hosting).

Backend services for this application are primarily **externally hosted**:
*   **Authentication**: Handled by **Clerk**, a cloud-hosted authentication service.
*   **Payments**: Handled by **Stripe**, a cloud-hosted payment processing service.
*   **Database**: Uses **Neon**, a serverless PostgreSQL provider, which is also cloud-hosted.
*   **API Routes**: The API routes defined in `app/(api)/` are typically deployed as **serverless functions**. These are not part of the mobile app bundle or static web build but are deployed separately to a cloud function provider (e.g., Vercel, Netlify Functions, AWS Lambda, or potentially via Expo Application Services).

### Mobile App Distribution (App Stores)

Submitting your compiled mobile app to the Google Play Store (Android) and Apple App Store (iOS) generally involves:
1.  **Developer Accounts**: You'll need to register for a Google Play Console account and an Apple Developer Program account.
2.  **App Listings**: Prepare necessary metadata for each store, including app name, description, screenshots, privacy policy URL, and categorization.
3.  **Build Release Versions**: Compile your app into the required format: Android App Bundle (`.aab`) or `.apk` for Android; an iOS App Store Package (`.ipa`) for iOS.
4.  **Store Configuration**: Within each store's console, set up details like pricing, regional availability, and content ratings.
5.  **Upload and Review**: Upload your app binary and submit it for review. Both stores have review processes to ensure apps meet their guidelines.
6.  **Release**: Once approved, you can release your app.

**Expo Application Services (EAS)** can greatly simplify these processes:
*   **EAS Build**: Automates the creation of app binaries (`.aab`, `.apk`, `.ipa`) in the cloud, removing the need for complex local build setups. More info: [EAS Build Documentation](https://docs.expo.dev/build/introduction/)
*   **EAS Submit**: Streamlines the process of uploading your binaries and submitting them to the app stores. More info: [EAS Submit Documentation](https://docs.expo.dev/submit/introduction/)

Always refer to the official Expo documentation and the respective app store guidelines for the most current and detailed information.

### Web Version Deployment

1.  **Creating a Web Build**:
    To generate the static files for your web app, run the following command in your project's root directory:
    ```bash
    npx expo export:web
    ```
    This command creates a `web-build` directory (or similar) containing your app's HTML, JavaScript, CSS, and other assets. For more details on web builds, consult the [Expo Web Deployment Documentation](https://docs.expo.dev/distribution/web-deployment/).

2.  **Hosting Static Web Content**:
    The contents of the `web-build` directory can be deployed to any static web hosting provider. Popular choices include:
    *   Vercel
    *   Netlify
    *   GitHub Pages
    *   AWS S3 (often used with CloudFront for CDN)
    *   Firebase Hosting
    The deployment process varies by provider. Generally, you'll connect your project (e.g., via Git or manual upload) and configure the publish directory to `web-build`. Always refer to the specific documentation of your chosen hosting provider for detailed instructions (e.g., Vercel: [Expo on Vercel](https://vercel.com/docs/frameworks/expo), Netlify: [Expo on Netlify](https://docs.netlify.com/configure-builds/common-configurations/expo/)).

### Backend Services and API Hosting

1.  **API Routes as Serverless Functions**:
    API routes within your project (e.g., in `app/(api)/`) are typically implemented as serverless functions (often Node.js). These are **not** bundled with your mobile or static web app but are deployed and run separately on a cloud platform. Your client application makes network requests to the URLs of these deployed functions.

2.  **Deployment of Serverless Functions**:
    These functions must be deployed to a platform supporting Node.js serverless functions, such as:
    *   Vercel (integrates well with Next.js, which Expo can use for web/API routes)
    *   Netlify Functions
    *   AWS Lambda
    *   Google Cloud Functions
    *   Azure Functions
    For potential Expo-specific solutions for deploying these functions, consult the [official Expo documentation](https://docs.expo.dev/), particularly any information regarding Expo Application Services (EAS). Also, refer to the documentation of your chosen serverless platform.

3.  **Externally Hosted Services**:
    Key backend functionalities rely on third-party cloud services, managed by their respective providers:
    *   **Database (Neon)**: You manage your serverless PostgreSQL instance via the Neon dashboard; your app connects using provided credentials.
    *   **Authentication (Clerk)**: User management and authentication are handled by Clerk; your app integrates using API keys configured in your Clerk dashboard.
    *   **Payments (Stripe)**: Payment processing is managed through your Stripe account; your app uses Stripe's SDKs and API keys.
    Your responsibility involves managing accounts with these providers and securely handling the API keys/credentials within your application environment.

## Author

Anil Rana

## License

MIT 
