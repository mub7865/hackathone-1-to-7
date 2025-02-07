# **Marketplace E-commerce System**

## **Overview**

This is a marketplace e-commerce platform developed using **Next.js 14** with **TypeScript**. The platform uses **Sanity CMS** for managing content and integrates **ShipEngine** for shipment tracking. The focus of this project is to offer trendy, affordable, and Pinterest-inspired furniture to customers.

---

## **Features**
- **Product Browsing**: View a variety of products with detailed information, categories, and filters.
- **User Cart**: Add products to the cart, manage quantities, and proceed to checkout.
- **Order Management**: Track orders, manage shipping, and receive real-time tracking updates.
- **Admin Panel**: Manage products, orders, and view analytics.
- **Payment Integration**: Secure payments using **Stripe**.
- **Shipment Tracking**: Real-time shipment tracking via **ShipEngine API**.

---

## **High-Level Architecture**

### **Frontend**
- **Framework:** Next.js 14 with TypeScript for server-side rendering (SSR).
- **Pages:**
  - **Home Page:** Displays featured products and promotions.
  - **Product Pages:** List products with sorting and filtering options.
  - **Cart:** Displays user’s selected items for purchase.
  - **Checkout:** Collects user’s details for order and payment.
  - **Admin Panel:** For managing products, orders, and inventory.
  - **User Portal:** Displays user’s order history and tracking details.

### **Backend**
- **API Endpoints:**
  - **Products API**: Fetches product details.
  - **Shipment API**: Creates and tracks shipments via **ShipEngine**.
  - **Order API**: Manages user orders and payment statuses.
  - **Live Tracking API**: Fetches real-time shipment status using tracking number.

### **CMS (Sanity)**
- **Sanity Studio** is used to manage:
  - **Products**: Name, description, price, images.
  - **Orders**: Tracks purchased items and shipment statuses.
  - **Users**: User profiles and authentication.

---

## **APIs**

### **Product API**
- **Endpoint:** `/api/products`
- **Method:** GET
- **Description:** Fetches details of all available products.

### **Shipment API**
- **Endpoint:** `/api/shipmentOrder`
- **Method:** POST
- **Description:** Creates a shipment and generates tracking info.
- **Request:**
  ```json
  {
    "from": {
      "name": "E-commerce Store",
      "street1": "123 Store Lane",
      "city": "San Francisco",
      "state": "CA",
      "zip": "94107",
      "country": "US"
    },
    "to": {
      "name": "John Doe",
      "street1": "456 User Street",
      "city": "New York",
      "state": "NY",
      "zip": "10001",
      "country": "US"
    },
    "parcel": {
      "length": "10",
      "width": "10",
      "height": "10",
      "weight": "5",
      "mass_unit": "lb"
    }
  }

### **Response:**

{
  "shipmentId": "987",
  "trackingNumber": "1234567890",
  "carrier": "shipengine",
  "eta": "2025-01-18T10:00:00Z",
  "status": "In Transit"
}

#### **Live Tracking API**
- **Endpoint:** `/api/liveTracking`
- **Method:** GET
- **Description:** Fetches real-time tracking details using the **ShipEngine API**.
- **Request Parameters:**
  - `carrier`: Carrier name (e.g., **ShipEngine**).
  - `trackingNumber`: The tracking number for the shipment.

---


### **Frontend:**
- **Next.js 14**
- **TypeScript**
- **Tailwind CSS** for styling

### **Backend:**
- **Node.js**
- **ShipEngine API** for shipment tracking
- **Stripe** for payment processing

### **CMS:**
- **Sanity CMS** for managing content and product data

### **Deployment:**
- **Vercel** for hosting the application
