# 🛠 BazarGo Architecture

## 📌 Overview

BazarGo is a **monolithic** eCommerce platform designed for ordering and delivering groceries and weekly essentials. The system allows users to:

- Order **immediate deliveries** or **schedule deliveries**.
- Manage products, carts, and orders efficiently.
- Support both **customers** and **admins** through separate frontends.

This document explains the **architecture, technologies, and structure** of BazarGo so that developers can easily understand and contribute.

---

## 🏗 System Architecture

BazarGo follows a **monolithic** architecture where both the backend and frontend exist as a single codebase but are structured **modularly**.

### 🖥️ Frontend (Web & Admin Panel)

- **Framework:** React (Vite)
- **Styling:** Tailwind CSS
- **Linting & Formatting:** ESLint & Prettier
- **State Management:** React Context API (or Redux if needed)
- **API Communication:** Fetch/Axios to connect with backend
- **Admin Panel:** Separate interface for managing orders, products, and users

**Why Vite?**

- Faster build times
- Better performance in development

---

### ⚙️ Backend

- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB (via Mongoose ORM)
- **Authentication:** JWT (JSON Web Tokens)
- **Validation:** Joi / Express Validator
- **Storage:** Cloud-based storage for product images (e.g., AWS S3, Cloudinary)
- **Logging & Debugging:** Winston / Morgan

**Why Monolithic Instead of Microservices?**  
✅ Simpler development and deployment  
✅ Easier to maintain as an open-source project  
✅ Less infrastructure complexity

> _In the future, if the project scales, we can consider a **modular monolith** or **microservices**._

---

## 🛢️ Database (MongoDB)

BazarGo uses **MongoDB** as the primary database.

### 📌 Key Collections

| Collection      | Purpose                                                |
| --------------- | ------------------------------------------------------ |
| `users`         | Stores user data (customers & admins)                  |
| `products`      | Stores product details (name, price, category, stock)  |
| `orders`        | Manages order data (status, delivery time, total cost) |
| `cart`          | Handles user carts before checkout                     |
| `notifications` | Stores user/admin notifications                        |
| `settings`      | App-wide settings for customization                    |

**Why MongoDB?**

- Flexible schema for evolving business needs
- Scales well for high-traffic applications

---

## 🔄 API Structure

BazarGo follows **RESTful API principles**.

| Method   | Endpoint             | Description               |
| -------- | -------------------- | ------------------------- |
| **POST** | `/api/auth/register` | Register a new user       |
| **POST** | `/api/auth/login`    | Login & get a JWT         |
| **GET**  | `/api/products`      | Get a list of products    |
| **POST** | `/api/cart/add`      | Add a product to the cart |
| **POST** | `/api/orders`        | Place an order            |

📌 **For a full list of API endpoints, check the [API Documentation](./api/api-docs.md).**

---

## 🛠 Deployment & DevOps

| Component                 | Technology                  |
| ------------------------- | --------------------------- |
| **Backend Hosting**       | AWS / DigitalOcean / Vercel |
| **Frontend Hosting**      | Vercel / Netlify            |
| **Database**              | MongoDB Atlas               |
| **CI/CD**                 | GitHub Actions              |
| **Logging**               | Winston, Morgan             |
| **Environment Variables** | `.env` file                 |

---

## 📌 Future Improvements

- **GraphQL API Support** – If API performance needs optimization
- **Microservices (Optional)** – If scaling beyond monolith is needed
- **Push Notifications** – Real-time order updates for users

---

## 🚀 Summary

- BazarGo is a **monolithic** eCommerce platform.
- Uses **React (Vite) for frontend**, **Node.js + Express for backend**, and **MongoDB** for the database.
- **RESTful API structure** for communication.
- **CI/CD, authentication, logging, and scalability considerations** are in place.

> _For any development questions, check the relevant docs or open an issue on GitHub._

---

## 📌 Next Steps

Would you like me to add a **diagram** to visually explain this architecture? 🚀📖
