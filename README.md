# 🛒 Gadget Shop

A web application for exploring and purchasing laptops and computers, featuring PayPal Sandbox payment integration using OAuth 2.0.

## 🚀 Features

- **Product Search**: Quickly find products by name or description.
- **Shopping Cart**: Add/remove items, view live total.
- **PayPal Checkout**: Secure payments via PayPal Sandbox (OAuth 2.0).
- **Responsive Design**: Works on desktop, tablet, and mobile.
- **Error Handling**: User-friendly error messages and loading indicators.

## 🛠️ Technologies Used

- HTML5
- CSS3
- JavaScript (ES6+)
- PayPal REST API

## 📦 Installation

1. **Clone the repository**
   ```sh
   git clone https://github.com/glennmarkpogi/PayPal_API.git
   ```
2. **Navigate to the project folder**
   ```sh
   cd Elect_Final_GroupingsV1/Paypal_API
   ```
3. **Configure PayPal credentials**
   - Open `config.js` and set your PayPal Sandbox `CLIENT_ID` and `SECRET`.
4. **Open `index.html` in your web browser**
   - Use VS Code Live Server or a simple HTTP server for best results.

## 🖥️ How to Use

1. Open `index.html` in your web browser.
2. Browse and search for products.
3. Add items to your cart.
4. Click "Proceed to PayPal Checkout" to start the payment process.
5. Complete the payment in the PayPal Sandbox window.
6. Return to the site to see your order status.

## 🧪 How to Run in Postman

You can test the PayPal API endpoints using Postman. Follow these steps:

### 1. Generate OAuth Token

- **Method:** POST
- **URL:** `https://api-m.sandbox.paypal.com/v1/oauth2/token`
- **Headers:**
   - `Content-Type: application/x-www-form-urlencoded`
- **Auth:**
   - Type: Basic Auth
   - Username: Your CLIENT_ID
   - Password: Your SECRET
- **Body (x-www-form-urlencoded):**
   - `grant_type=client_credentials`
- **Expected:** 200 OK with `access_token` in the response

### 2. Create Order

- **Method:** POST
- **URL:** `https://api-m.sandbox.paypal.com/v2/checkout/orders`
- **Headers:**
   - `Authorization: Bearer YOUR_ACCESS_TOKEN`
   - `Content-Type: application/json`
- **Body (raw JSON):**
   ```json
   {
      "intent": "CAPTURE",
      "purchase_units": [{
         "amount": {
            "currency_code": "USD",
            "value": "1200.00"
         }
      }]
   }
   ```
- **Expected:** 201 Created with order ID and approve link

### 3. Capture Order

- **Method:** POST
- **URL:** `https://api-m.sandbox.paypal.com/v2/checkout/orders/{ORDER_ID}/capture`
- **Headers:**
   - `Authorization: Bearer YOUR_ACCESS_TOKEN`
   - `Content-Type: application/json`
- **Body:** (empty)
- **Expected:** 201 with COMPLETED status

---


## 🐛 Troubleshooting

- **Authentication failed:** Check your CLIENT_ID and SECRET in `config.js` and ensure you are using Sandbox credentials.
- **CORS error:** Run the project on a local server (not by opening the HTML file directly).
- **Order creation failed:** Check your internet connection and ensure the access token is valid.

## 📚 API Reference (PayPal)

**Base URL:** `https://api-m.sandbox.paypal.com`

**Endpoints:**
- `/v1/oauth2/token` — Generate OAuth token
- `/v2/checkout/orders` — Create order
- `/v2/checkout/orders/{order_id}/capture` — Capture order

**Required Parameters:**
- OAuth 2.0 authentication (client credentials)
- Bearer token for order endpoints

**Authentication:**
- OAuth 2.0 (client credentials flow)

**Sample JSON Response (Order):**
```json
{
  "id": "ORDER_ID",
  "status": "CREATED",
  "links": [
    { "href": "https://www.sandbox.paypal.com/checkoutnow?token=ORDER_ID", "rel": "approve", "method": "GET" }
  ]
}
```

## Screenshot
![App Screenshot](Screenshot.png)

## 📄 License

This project is open source and free to use for educational purposes.

## Members & Roles
- **Glenn Mark Jimenez**       — Lead Developer, API & Authentication Handler, Testing
- **Ralph Royet Delos Santos** — JavaScript Logic / Data Processing
- **Mark Dave Esteron**        — UI/UX & CSS Designer, GitHub & Documentation Manager

---

**Powered by PayPal Sandbox API** 🚀



