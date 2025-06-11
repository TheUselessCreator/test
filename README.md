
# Discord Bot Hosting Platform - Setup Guide

## 📋 Prerequisites
Before setting up the project, make sure you have the following installed:
````
- [Node.js (v18 or higher)](https://nodejs.org/)  
- npm (comes with Node.js)  
- [Visual Studio Code](https://code.visualstudio.com/)  
- [Git (optional but recommended)](https://git-scm.com/)  
````


## 🚀 Initial Setup

### 1️⃣ Create Project Directory
````
mkdir discord-bot-hosting-platform
cd discord-bot-hosting-platform
````

### 2️⃣ Initialize the Project

Copy all the provided files into your project directory, maintaining this folder structure:

```
discord-bot-hosting-platform/
├── src/
│   ├── components/
│   ├── hooks/
│   ├── types/
│   └── ...
├── server/
├── data/
├── package.json
└── ...
```

### 3️⃣ Install Dependencies

Open terminal in Visual Studio Code (Ctrl + \`) and run:

```
npm install
```

This will install all required packages including:

* Frontend: React, TypeScript, Tailwind CSS, Lucide React
* Backend: Express, WebSocket, CORS, UUID
* Development: Vite, ESLint, Concurrently, TSX

---

## ⚙️ Configuration

### 1️⃣ Configure Discord Application

* Go to [Discord Developer Portal](https://discord.com/developers/applications).
* Create a new application.
* Go to **OAuth2** and add **redirect URI:** `http://localhost:3000/auth/callback`.
* Copy your **Client ID** and **Client Secret**.

### 2️⃣ Update `data/config.json`:

```json
{
  "HOSTNAME": "localhost:3000",
  "MAX_BOTS_PER_USER": 2,
  "AUTO_SHUTDOWN_TIMER": 3600000,
  "AUTO_DELETE_DAYS": 7,
  "OWNER_ID": "YOUR_DISCORD_USER_ID_HERE",
  "DISCORD_CLIENT_ID": "your_discord_client_id_here",
  "DISCORD_CLIENT_SECRET": "your_discord_client_secret_here"
}
```

To find your Discord User ID:

* Enable Developer Mode in Discord (User Settings > Advanced).
* Right-click your username and select **Copy ID**.

---

## 🏃‍♂️ Running the Application

### Development (Recommended)

```
npm run dev
```

This will:

* Run the React frontend at `http://localhost:5173`
* Run the Express backend at `http://localhost:3001`

---

### Individual

```
npm run dev:client  # Frontend only
npm run dev:server  # Backend only
```

---

### Build for production:

```
npm run build
```

Then preview:

```
npm run preview
```

---

## 🔧 Visual Studio Code Setup (Optional)

### Recommended Extensions:

* **ES7+ React/Redux snippets**
* **TypeScript Importer**
* **Tailwind CSS IntelliSense**
* **Auto Rename Tag**
* **Bracket Pair Colorizer**
* **ESLint**
* **Prettier**

### `.vscode/settings.json`:

```json
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "tailwindCSS.includeLanguages": {
    "typescript": "typescript",
    "typescriptreact": "typescriptreact"
  },
  "files.associations": {
    "*.css": "tailwindcss"
  }
}
```

---

## 📁 Project Structure

```
discord-bot-hosting-platform/
├── src/
│   ├── components/
│   ├── hooks/
│   ├── types/
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── server/
│   └── index.ts
├── data/
│   ├── config.json
│   ├── users.json
│   └── bots/
├── package.json
├── vite.config.ts
├── tailwind.config.js
├── tsconfig.json
```

---

## 🔐 Security Notes

* Bot tokens are stored in `data/bots/{botId}`.
* Do **not** commit tokens to Git.
* `OWNER_ID` controls administrative privilege.
* WebSocket messages are routed per bot.

---

## 🐛 Troubleshooting

### Port already in use:

```
npx kill-port 3001 5173
```

### Dependencies not installing:

```
npm cache clean --force
rm -rf node_modules package-lock.json
npm install
```

### TypeScript errors:

```
Ctrl + Shift + P > "TypeScript: Restart TS Server"
```

### Tailwind not loading:

* Confirm `src/index.css` includes:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

* Restart dev server afterwards.

---

## Development Tips

✅ `Ctrl + Shift + P`: VSCode Command Palette
✅ \`Ctrl + \`\` : Integrated terminal
✅ [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client) for API testing
✅ [React Developer Tools](https://chrome.google.com/webstore/detail/react-development-tool) for UI debug

---

## 🚀 Production Deployment

```
npm run build
```

* Update `config.json` with proper `HOSTNAME`.
* Set environment variables.
* Use **pm2** to run backend:

```
npm install -g pm2
pm2 start server/index.ts --name "bot-hosting-backend"
```

---

## 📞 Support

If you encounter issues:

* Check the **browser console** for frontend errors.
* Check the **terminal/server logs** for backend errors.
* Validate **Discord application configuration**.
* Confirm **ports 3001 and 5173** are available.

---

✅ The platform is now ready for development!
Start it with:

```
npm run dev
```

and navigate to [http://localhost:5173](http://localhost:5173) to see your **Discord Bot Hosting Platform** in action.

```


