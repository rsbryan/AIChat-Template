AIChat - iOS AI Chatbot App
A simple and secure iOS chatbot app built with Expo React Native that connects to OpenAI's GPT models through a secure backend proxy.

Features
🤖 AI-powered conversations using OpenAI GPT
📱 Native iOS experience with Expo
🔒 Secure API key protection through backend proxy
💬 Text message-like UI interface
⚡ Real-time chat responses
Architecture
AIChat App → Secure Backend → OpenAI API
This app doesn't store OpenAI API keys locally - all requests go through a secure backend that handles API key management.

Prerequisites
Node.js 18+
Expo CLI
iOS Simulator or physical iOS device
A deployed backend proxy (see backend repo)
Setup
Clone the repository:
bash
git clone https://github.com/yourusername/aichat-app.git
cd aichat-app
Install dependencies:
bash
npm install
Create environment file:
bash
cp .env.example .env
Configure your environment variables in .env:
EXPO_PUBLIC_API_URL=https://your-backend.vercel.app
EXPO_PUBLIC_API_KEY=your-app-key
Start the development server:
bash
expo start
Run on iOS:
Press i for iOS simulator
Or scan QR code with Expo Go app on your device
Environment Variables
Variable	Description	Example
EXPO_PUBLIC_API_URL	Your backend API URL	https://your-backend.vercel.app
EXPO_PUBLIC_API_KEY	Authentication key for your backend	your-secure-app-key
Project Structure
aichat-app/
├── App.js              # Main app component
├── assets/             # Images and icons
├── components/         # Reusable UI components
├── services/           # API service functions
├── .env.example        # Environment variables template
└── package.json        # Dependencies and scripts
API Integration
The app communicates with a secure backend proxy instead of calling OpenAI directly:

javascript
// Instead of calling OpenAI directly (insecure)
// This app calls your secure backend
const response = await fetch(`${API_URL}/api/chat`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-API-Key': API_KEY
  },
  body: JSON.stringify({ messages })
});
Security Features
✅ No API keys stored in client code
✅ All requests authenticated with app key
✅ Backend handles all OpenAI communication
✅ Rate limiting protection
✅ CORS protection
Backend Repository
This app requires a secure backend proxy. Set up the backend first: Repository: openai-proxy-backend

Development
Running Locally
bash
npm start
# or
expo start
Building for Production
bash
expo build:ios
Troubleshooting
Common Issues:

"Network Error" or API calls failing:
Check your .env file has correct backend URL
Ensure backend is deployed and running
Verify APP_KEY matches between app and backend
Expo app won't start:
Clear Expo cache: expo start -c
Reinstall dependencies: rm -rf node_modules && npm install
iOS Simulator issues:
Restart simulator
Check Xcode is properly installed
Contributing
Fork the repository
Create a feature branch: git checkout -b feature-name
Commit changes: git commit -m 'Add feature'
Push to branch: git push origin feature-name
Open a Pull Request
License
MIT License - see LICENSE file for details

Related Projects
OpenAI Proxy Backend - Secure API proxy for this app
⚠️ Security Note: Never commit API keys or sensitive credentials to this repository. All sensitive configuration should be in .env files which are ignored by git.

