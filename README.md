# 🛒 Gadget Shop - PayPal REST API Integration

A complete mini e-commerce platform for laptops and computers with PayPal Sandbox payment integration using OAuth 2.0.

## ✅ Project Requirements Met (16/16)

### 1. Base URL ✔
- PayPal Sandbox API: `https://api-m.sandbox.paypal.com`

### 2. Endpoints Used ✔
- **OAuth Token**: `POST /v1/oauth2/token`
- **Create Order**: `POST /v2/checkout/orders`
- **Capture Order**: `POST /v2/checkout/orders/{order_id}/capture`

### 3. Required Parameters ✔
- All headers, body parameters, and path parameters implemented
- OAuth authentication with Base64 encoded credentials
- Bearer token for API requests

### 4. Authentication ✔
- OAuth 2.0 implementation
- Client credentials flow
- Secure token management

### 5. Sample JSON Response ✔
- Order ID, status, and approval links displayed
- Proper field mapping in UI

### 6. API Testing (POSTMAN) ✔
**Test all three endpoints:**
1. Generate OAuth Token
2. Create Order
3. Capture Order (optional - requires approved order)

### 7. Fetch Data ✔
- `async/await` with `fetch()` API
- Proper error handling with try/catch

### 8. Display Data in HTML ✔
- Product cards with images, names, prices
- Shopping cart display
- Order information display

### 9. Error Handling ✔
- Empty cart validation
- Invalid price checks
- API failure messages
- Authentication errors
- Network errors

### 10. Input Validation ✔
- Search input trimming
- Cart validation before checkout
- Numeric price validation

### 11. Loading State ✔
- Spinner animation during API calls
- Button disabling during processing

### 12. Responsive Design ✔
- Mobile-first CSS
- Flexbox and Grid layouts
- Breakpoints: 768px, 480px

### 13. File Requirements ✔
```
/Paypal_API
├── index.html    (Structure)
├── style.css     (Styling)
├── script.js     (Logic)
└── config.js     (API Keys)
```

### 14. Code Organization ✔
- Separated concerns (HTML/CSS/JS)
- Modular functions
- No code duplication

### 15. UI Requirements ✔
- Search bar
- Product cards with Buy buttons
- Shopping cart
- Error/Success containers
- Footer with API credit

### 16. API Key Security ✔
- Stored in `config.js`
- ES6 module imports
- Placeholders for safety

---

## 🚀 Setup Instructions

### Step 1: Get PayPal Credentials
1. Go to [PayPal Developer Dashboard](https://developer.paypal.com/dashboard/)
2. Log in (or create account)
3. Navigate to **Apps & Credentials**
4. Create a new app (Sandbox mode)
5. Copy your **Client ID** and **Secret**

### Step 2: Configure the Project
1. Open `config.js`
2. Replace placeholders:
```javascript
export const CLIENT_ID = "Your_Actual_Client_ID";
export const SECRET = "Your_Actual_Secret_Key";
```

### Step 3: Run the Project
**Option 1: Live Server (Recommended)**
- Install VS Code extension: "Live Server"
- Right-click `index.html` → Open with Live Server

**Option 2: Simple HTTP Server**
```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server -p 8000
```

Then open: `http://localhost:8000`

---

## 📋 POSTMAN Testing Guide

### Test 1: Generate OAuth Token
```
Method: POST
URL: https://api-m.sandbox.paypal.com/v1/oauth2/token

Headers:
- Content-Type: application/x-www-form-urlencoded

Auth:
- Type: Basic Auth
- Username: YOUR_CLIENT_ID
- Password: YOUR_SECRET

Body (x-www-form-urlencoded):
grant_type = client_credentials

Expected: 200 OK with access_token
```

### Test 2: Create Order
```
Method: POST
URL: https://api-m.sandbox.paypal.com/v2/checkout/orders

Headers:
- Authorization: Bearer YOUR_ACCESS_TOKEN
- Content-Type: application/json

Body (raw JSON):
{
  "intent": "CAPTURE",
  "purchase_units": [{
    "amount": {
      "currency_code": "USD",
      "value": "1200.00"
    }
  }]
}

Expected: 201 Created with order ID and approve link
```

### Test 3: Capture Order
```
Method: POST
URL: https://api-m.sandbox.paypal.com/v2/checkout/orders/{ORDER_ID}/capture

Headers:
- Authorization: Bearer YOUR_ACCESS_TOKEN
- Content-Type: application/json

Body: (empty)

Expected: 201 with COMPLETED status
```

---

## 🎯 Features

- **6 Premium Products**: Laptops and computers with real descriptions
- **Shopping Cart**: Add/remove items with live total
- **Search Functionality**: Filter products by name or description
- **PayPal Integration**: Secure Sandbox checkout
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Error Handling**: User-friendly error messages
- **Loading States**: Visual feedback during API calls

---

## 🛠 Technologies Used

- **HTML5**: Semantic structure
- **CSS3**: Flexbox, Grid, animations
- **JavaScript (ES6+)**: Modules, async/await, fetch
- **PayPal REST API**: Payment processing
- **OAuth 2.0**: Secure authentication

---

## 📱 Responsive Breakpoints

- **Desktop**: > 768px (grid layout)
- **Tablet**: 481px - 768px (2 columns)
- **Mobile**: ≤ 480px (single column)

---

## ⚠️ Important Notes

1. **Sandbox Mode Only**: This uses PayPal Sandbox for testing
2. **No Real Payments**: All transactions are simulated
3. **Config Security**: Never commit `config.js` with real credentials
4. **CORS**: Must run on a server (not `file://`)

---

## 🐛 Troubleshooting

### "Authentication failed"
- Check CLIENT_ID and SECRET in `config.js`
- Verify credentials are from Sandbox, not Live

### "CORS error"
- Run on a local server (Live Server, http-server)
- Don't open HTML file directly in browser

### "Order creation failed"
- Check internet connection
- Verify access token is valid
- Ensure amount is formatted correctly (e.g., "1200.00")

---

## 📚 API Documentation

- [PayPal REST API Docs](https://developer.paypal.com/docs/api/overview/)
- [Orders API Reference](https://developer.paypal.com/docs/api/orders/v2/)
- [OAuth 2.0 Guide](https://developer.paypal.com/api/rest/authentication/)

---

## 👨‍💻 Demo Flow

1. Browse 6 laptop products
2. Add items to cart
3. View cart summary with total
4. Click "Proceed to PayPal Checkout"
5. Order created (ID displayed)
6. Click "Complete Payment on PayPal"
7. Redirected to PayPal Sandbox
8. Log in with test account
9. Approve payment
10. Return to site (order captured)

---

## 📄 License

This is a student project for educational purposes.

---

## 🎓 Assignment Checklist

- [x] Base URL documented
- [x] 3 Endpoints implemented
- [x] Required parameters listed
- [x] OAuth 2.0 authentication
- [x] JSON response handling
- [x] POSTMAN testing screenshots
- [x] Fetch API implementation
- [x] DOM display
- [x] Error handling
- [x] Input validation
- [x] Loading indicators
- [x] Responsive CSS
- [x] Separate files (no inline)
- [x] Organized code
- [x] Complete UI elements
- [x] Secure config.js

---

**Powered by PayPal Sandbox API** 🚀
