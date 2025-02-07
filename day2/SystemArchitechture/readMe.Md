# Marketplace E-commerce System Architecture

## Overview
This document outlines the system architecture of a marketplace e-commerce platform developed using Next.js 14 with TypeScript. The platform leverages Sanity as a content management system (CMS) and includes features for users, administrators, and shipment tracking.

---

## High-Level System Architecture

### **Frontend Structure**
- **Framework:** Next.js 14 with TypeScript for server-side rendering (SSR) and dynamic routing.
- **Pages:**
  - **Home:** Displays featured products and promotional banners.
  - **Products:** Displays all available products with filtering and sorting options.
  - **Product Details:** Dynamic route for detailed product information.
  - **Cart:** Manages user-selected items for purchase.
  - **Checkout:** Handles user details and payment processes.
  - **Admin Panel:** For site management, including analytics and inventory control.
  - **User Portal:** Displays order history, shipment details, and account settings.

### **Reusable Components**
- **CardComponent.tsx:** Displays product information.
- **HeroSection.tsx:** Highlights promotional offers.
- **Listing.tsx, PopularProducts.tsx:** Organize and display product categories and highlights.

---

## **CMS (Sanity)**

### **Sanity Studio**
Used to manage:
- **Products:** Information such as name, price, images, and descriptions.
- **Users:** Authentication and order history.
- **Orders:** Tracks purchased items and shipping details.
- **Inventory:** Manages stock levels.

### **Data Management**
- **Schemas:**
  - Products
  - Orders
  - Users
  - Inventory
  - Shipments
- **GROQ Queries:** Fetch data dynamically for frontend rendering.

---

## **Backend Features**

### **Mock APIs**
- Simulate server-side logic and data management.
- **Endpoints:**
  - `/api/products`: Fetch product data.
  - `/api/orders`: Handle order creation and tracking.
  - `/api/shipments`: Manage shipment creation and tracking.

### **Payment Gateway (Stripe)**
- **Integration:** Handles secure transactions.
- **Components:** Stripe Elements for collecting payment information.

### **Shipment Tracking (Shippo API)**
- Provides shipment details and real-time tracking.
- **Endpoints:**
  - `/api/shipments`: Creates shipment orders.
  - `/api/liveTracking`: Fetches live tracking data.

---

## **Workflow Overview**

### **User Workflow**
1. **Browse Products:**
   - Products dynamically fetched from Sanity.
2. **Add to Cart:**
   - Cart managed locally until user login.
3. **Checkout:**
   - User provides payment and shipping details.
4. **Order Confirmation:**
   - Data stored in Sanity and displayed in the User Portal.
5. **Track Shipment:**
   - Shipment tracking through Shippo API.

### **Admin Workflow**
1. **Login:**
   - Admin access secured with credentials.
2. **Manage Products:**
   - Add, edit, or remove products.
3. **Monitor Orders:**
   - View and update order status.
4. **View Analytics:**
   - Detailed insights into sales and trends.

---

## **Technologies and Tools**
- **Frontend:** Next.js 14 with TypeScript
- **CMS:** Sanity
- **Payment Gateway:** Stripe
- **Shipment Tracking:** Shippo API
- **Deployment:** Vercel

---

## **Folder Structure**
```
/project-root
  /src
    /app
      /about        // About page
      /cart         // Shopping cart page
      /products     // Products listing
      /[id]         // Dynamic product detail pages
      /contact      // Contact page
      /user         // User profile and order details
      /admin        // Admin panel
    /sanity
      /schemaTypes
        analytics.ts
        users.ts
        orders.ts
        shipments.ts
        products.ts
    /types
      componentTypes.ts
    /components
      /adminPanel
        Analytics.tsx
        Dashboard.tsx
        Orders.tsx
        Stock.tsx
      /heroSection
        Hero.tsx
        Listing.tsx
      /reusableComponents
        ProductCard.tsx
        FeatureCard.tsx
    /orderSystem
      CheckoutModal.tsx
      PaymentForm.tsx
    /userPortal
      LoginPortal.tsx
      UserDetail.tsx
```

---

## **Data Flow**
1. **Products:**
   - Stored in Sanity, displayed dynamically on the frontend.
2. **User Cart:**
   - Managed locally, synced with server upon login.
3. **Orders:**
   - Stored in Sanity and accessible by both users and admins.
4. **Payments:**
   - Processed securely via Stripe.
5. **Shipments:**
   - Tracked using the Shippo API.

