# Hosting a React Native (Expo) App

This document explains how a React Native application built with Expo is "hosted" and made available to users, covering both mobile and web deployments, as well as backend services.

## 1. Mobile App "Hosting" is Distribution

For mobile applications targeting iOS and Android, "hosting" is fundamentally about **distribution**. Once your Expo app is developed and tested, you'll build a compiled version of your application. This compiled package (e.g., `.ipa` for iOS, `.aab` or `.apk` for Android) is then submitted to:

*   **Apple App Store**: For iOS users to download and install on their iPhones and iPads.
*   **Google Play Store**: For Android users to download and install on their Android devices.

These app stores handle the infrastructure for delivering your app to end-users. Expo Application Services (EAS) can simplify the build and submission process for these stores.

## 2. Web Version Hosting

Expo allows you to build your React Native application as a progressive web app (PWA) or a standard web application. When you create a web build, the output consists of static files: HTML, CSS, and JavaScript.

These static files can be deployed to any **static web hosting service**. Popular options include:

*   Vercel
*   Netlify
*   AWS S3 with CloudFront
*   GitHub Pages
*   Firebase Hosting

These services specialize in serving static content efficiently and often offer features like global content delivery networks (CDNs) and custom domain support.

## 3. Backend Services are Externally Hosted

Modern applications, including those built with Expo, often rely on various backend services. These services are typically cloud-hosted and managed independently of your mobile app bundle or static web files. For this application, the backend services include:

*   **Authentication**: User authentication is managed by **Clerk**. Clerk is a third-party, cloud-hosted service that provides robust authentication and user management features. Your Expo app communicates with Clerk's APIs to sign users in, manage sessions, and protect routes.

*   **Payments**: Payment processing is handled by **Stripe**. Stripe is another third-party, cloud-hosted service that offers secure payment gateway functionalities. Your app integrates with Stripe's SDKs and APIs to process transactions.

*   **Database**: The application's database is powered by **Neon**, a serverless PostgreSQL provider. Neon is cloud-hosted, and your application connects to it to store and retrieve data.

*   **API Routes**: The API routes defined within the `app/(api)/` directory of your Expo project are typically deployed as **serverless functions**. These functions are not bundled directly into the mobile app or the static web build. Instead, they are deployed to a cloud function provider. When your app makes an API call to these routes, it's actually communicating with these deployed serverless functions. Examples of platforms that can host these include:
    *   Vercel (often used with Next.js, which Expo can integrate with for web)
    *   Netlify Functions
    *   AWS Lambda
    *   Expo Application Services (EAS) Functions

In summary, while the mobile app is distributed via app stores and the web version via static hosting, the core backend logic and data management rely on specialized, externally hosted cloud services. This architecture allows for scalability, security, and focused development.
