# 🛠️ Fixing CORS Issues in a React + Express App

## 🚀 Issue: CORS Policy Blocking Requests

### **Error Message:**

```
Access to fetch at 'http://localhost:3003/weather/Bangkok' from origin 'http://127.0.0.1:5173' has been blocked by CORS policy: The 'Access-Control-Allow-Origin' header has a value 'http://localhost:5173' that is not equal to the supplied origin.
```

### **🧐 What Causes This?**

- Your backend **only allows `localhost:5173`**.
- But your frontend might be using **`127.0.0.1:5173`** instead.
- Even though `localhost` and `127.0.0.1` refer to the same machine, **CORS treats them as different origins**.
- Some browsers (like Chrome) might default to `127.0.0.1`, causing unexpected errors.

---

## ✅ **Solution: Update CORS in `server.js`**

To allow **both `localhost` and `127.0.0.1`**, update your **Express CORS settings**:

```js
import cors from "cors";

app.use(
  cors({
    origin: ["http://localhost:5173", "http://127.0.0.1:5173"],
  })
);
```

### **🔹 If You Just Want to Allow All Origins (For Testing Only)**

```js
app.use(cors({ origin: "*" }));
```

⚠️ **Warning:** Allowing `*` is fine for development but is **not recommended for production** because it makes your API publicly accessible.

---

## 🔄 **Steps to Apply the Fix**

1️⃣ **Update your `server.js` file** with the new CORS settings.
2️⃣ **Restart your backend server** to apply changes:

```sh
npm run dev
```

3️⃣ **Check your frontend's URL**:

- If it's `127.0.0.1:5173`, manually switch to `localhost:5173` in the browser.
  4️⃣ **Test API requests again** from your frontend.

---

## 🎯 **Why Did This Happen?**

- Some operating systems resolve `localhost` differently from `127.0.0.1`.
- Chrome sometimes defaults to `127.0.0.1`.
- CORS **strictly checks** the **exact** origin, so `localhost` ≠ `127.0.0.1`.

---

## 🎉 **Issue Fixed!**

By allowing both `localhost` and `127.0.0.1`, your frontend can now access the backend without CORS errors. 🚀

If you're still facing issues, double-check your **server restart**, **browser console logs**, and **network requests in DevTools** (`F12 > Network`). 😊
