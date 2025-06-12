Digital Wallet React Application
A modern, responsive digital wallet application built with React.js that allows users to manage their wallet balance and track transactions.

# URL
https://wallet-system-frontend-rose.vercel.app/

# Features:

🏦 Wallet Management: Create and manage digital wallets with custom names
💰 Balance Tracking: Real-time balance updates and display
📊 Transaction History: Complete transaction logging with pagination
🔄 Transaction Processing: Add credit transactions with descriptions
📈 Sorting & Filtering: Sort transactions by date or amount
📤 Export Functionality: Export transaction history to CSV
🔄 Real-time Updates: Automatic balance and transaction refresh
📱 Responsive Design: Mobile-friendly interface

# Tech Stack

Frontend: React.js 18+ with Hooks
Styling: CSS
State Management: React Hooks (useState, useCallback, useMemo)
API Communication: Fetch API
Build Tool: Vite

#Prerequisites
Before running this application, make sure you have:

Node.js (version 16 or higher)
npm or yarn package manager
A backend API server running on http://localhost:3000 (see API Requirements section)

# Installation

Clone the repository
bash git clone <repository-url>
cd digital-wallet-app

Install dependencies
bash npm install

Install required dependencies
bash npm install react react-dom

## Project Structure

src/ <br>
├── api/ <br>
│   └── walletApi.js          # API service layer <br>
├── hooks/ <br>
│   ├── useWallet.js          # Main wallet state management <br>
│   └── useTransactionTable.js # Transaction table logic <br>
├── components/ <br>
│   ├── UI/ <br>
│   │   ├── Button.jsx        # Reusable button component<br>
│   │   ├── Input.jsx         # Form input component <br>
│   │   ├── Card.jsx          # Card container component <br>
│   │   ├── LoadingSpinner.jsx # Loading indicator <br>
│   │   └── ErrorMessage.jsx  # Error display component <br>
│   ├── Wallet/<br>
│   │   ├── WalletSetup.jsx   # Initial wallet creation<br>
│   │   ├── WalletBalance.jsx # Balance display <br>
│   │   └── TransactionForm.jsx # Add transaction form <br>
│   └── Transactions/ <br>
│       ├── TransactionTable.jsx # Transaction list table <br>
│       └── Pagination.jsx    # Table pagination <br>
├── pages/ <br>
│   ├── WalletPage.jsx        # Main wallet page <br>
│   └── TransactionsPage.jsx  # Transaction history page <br>
├── utils/ <br>
│   ├── apiHelpers.js         # Error handling  <br>
│   ├── csvExport.js          # CSV export functionality <br>
│   └── formatters.js         # Data formatting utilities <br>
└── App.jsx                   # Main application component <br>

# Setup Instructions
1. Update API Configuration
In src/api/walletApi.js, update the API base URL if needed:
javascriptconst API_BASE_URL = 'http://localhost:3000' // Update this URL
2. Setup Main Entry Point
Ensure your src/index.js or src/main.jsx looks like this:
jsximport React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
Running the Application

Start the development server
bash npm run dev
or
npm start

Open your browser
Navigate to http://localhost:5173 (or the port shown in terminal)

# API Requirements
This application expects a backend API with the following endpoints:
Required Endpoints

POST /setup - Create a new wallet
json{
  "name": "string",
  "balance": "number"
}

POST /transact/:walletId - Create a transaction
json{
  "amount": "number",
  "description": "string"
}

GET /transactions?walletId=:id&skip=:skip&limit=:limit - Get transactions
GET /wallet/:id - Get wallet details

Expected Response Format
Wallet Response:
json{
  "id": "string",
  "name": "string",
  "balance": "number",
  "date": "ISO date string"
}
Transaction Response:
json[
  {
    "id": "string",
    "amount": "number",
    "type": "CREDIT|DEBIT",
    "description": "string",
    "date": "ISO date string",
    "balance": "number"
  }
]

# Usage Guide
1. Creating a Wallet

Enter a wallet name (required)
Optionally set an initial balance
Click "Create Wallet"

2. Adding Transactions

Enter a positive amount
Add a description
Click "Add Transaction"

3. Viewing Transaction History

Click "View Transaction History" from the main page
Use sorting options by clicking column headers
Navigate through pages using pagination controls
Export data using the "Export CSV" button

Configuration Options
Customizing Items Per Page
In TransactionsPage.jsx, modify the pagination:
jsxconst { ... } = useTransactionTable(transactions, 10)
Changing Currency Format
In utils/formatters.js, update the currency formatter
Building for Production
bash npm run build

This creates a build (or dist) folder with optimized production files.

# Debug Mode
Add this to see API requests in console:
javascript// In walletApi.js, uncomment console.log statements
console.log('API request:', url, config)
Contributing

# Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add some amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request

Note: This application requires a compatible backend API to function properly. Make sure your backend server is running and accessible before starting the React application.
