# Laravel + React + TypeScript (Vite-Powered) Fullstack Starter

This project is a fullstack boilerplate using:

-   ✅ Laravel 12.x (API backend)
-   ✅ React + TypeScript (frontend)
-   ✅ Vite (asset bundling)
-   ✅ Single project architecture (React served via Blade)
-   ✅ API-ready for mobile, web, or dashboard usage

---

## 📦 Installation & Setup

### 1. Create Laravel Project

```bash
laravel new my-app
cd my-app
```

Or use Composer:

```bash
composer create-project laravel/laravel my-app
cd my-app
```

---

### 2. Install React + TypeScript + Vite Plugin

```bash
npm install
npm install react react-dom @vitejs/plugin-react
npm install --save-dev typescript @types/react @types/react-dom
npx tsc --init
```

Update `vite.config.js`:

```js
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";
import react from "@vitejs/plugin-react";

export default defineConfig({
    plugins: [
        laravel({
            input: ["resources/js/app.tsx"],
            refresh: true,
        }),
        react(),
    ],
});
```

Update `tsconfig.json`:

```json
{
    "compilerOptions": {
        "jsx": "react-jsx",
        "module": "ESNext",
        "target": "ESNext",
        "moduleResolution": "node",
        "strict": true,
        "esModuleInterop": true,
        "skipLibCheck": true,
        "forceConsistentCasingInFileNames": true
    }
}
```

---

## 📁 Project Structure

```
resources/js/
├── app.tsx         # React entry point
├── components/
│   └── App.tsx     # Main app component
├── pages/
├── hooks/
├── services/
├── utils/
```

---

## ⚛️ React App Files

### `resources/js/app.tsx`

```tsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./components/App";

const root = ReactDOM.createRoot(document.getElementById("app")!);
root.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>
);
```

### `resources/js/components/App.tsx`

```tsx
import React from "react";

const App: React.FC = () => (
    <div style={{ padding: "2rem" }}>
        <h1>Laravel + React + TypeScript ✅</h1>
    </div>
);

export default App;
```

---

## 🖼️ Blade Template

Create `resources/views/app.blade.php`:

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>React App</title>
    @viteReactRefresh
    @vite('resources/js/app.tsx')
</head>
<body>
    <div id="app"></div>
</body>
</html>
```

Update `routes/web.php`:

```php
Route::get('/', function () {
    return view('app');
});
```

---

## 🔗 API Setup

### 1. Install Laravel API Starter (Laravel 12+)

```bash
php artisan install:api
```

### 2. Add Test Route in `routes/api.php`

```php
Route::get('/ping', function () {
    return response()->json([
        'message' => 'API is working ✅',
        'time' => now(),
    ]);
});

Route::fallback(function () {
    return response()->json([
        'message' => 'API not found ❌',
        'time' => now(),
    ], 404);
});
```

Visit:  
http://127.0.0.1:8000/api/ping

---

## 🧪 Local Dev Commands

```bash
# Start Laravel
php artisan serve

# Start Vite dev server
npm run dev

# View app at:
http://127.0.0.1:8000

# API test:
http://127.0.0.1:8000/api/ping
```

---

## 🚀 Production Build

### 1. Build React + TypeScript Assets

```bash
npm run build
```

### 2. Set Environment in `.env`

```env
APP_ENV=production
APP_DEBUG=false
```

### 3. Optimize Laravel

```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan storage:link
```

---

## 📌 Notes & Tips

-   Keep `@vite('resources/js/app.tsx')` in your Blade — Laravel will switch between dev and production automatically.
-   Use **Sanctum** or **Passport** for authentication if needed.
-   For multi-surface apps (e.g. admin, mobile), you can add custom route groups and folders (`/admin`, `/api`, etc.).
-   In production, make sure Vite assets are built and available in `public/build/`.

---

## 📂 Useful Artisan Commands

```bash
php artisan route:list        # Show routes
php artisan config:clear      # Clear config cache
php artisan route:clear       # Clear route cache
php artisan view:clear        # Clear compiled views
```

---

## 🧠 TODO Suggestions

-   [ ] Add React Router for page navigation
-   [ ] Connect frontend to API with Axios
-   [ ] Add Auth flow with Laravel Sanctum
-   [ ] Role-based dashboard support
-   [ ] Deploy using Forge, Docker, or VPS

---

## 🧡 Built With

-   Laravel 12.x
-   React 18+
-   TypeScript
-   Vite

---

## 👤 Author

**Mustaf Abubakar**  
🔗 Website: [mustafabubakar.com](http://mustafabubakar.com)  
📧 Email: [me@mustafabubakar.com](mailto:me@mustafabubakar.com)
