🏨 Hotel Booking Service – Backend Microservice
A robust, production-grade hotel booking microservice built with Node.js, TypeScript, Express, Prisma, MySQL, and Redis. This service ensures idempotent booking operations and safe retry handling using Redlock-based distributed locking.

🚀 Features
✅ Idempotent Booking API using Redis and Redlock to prevent duplicate bookings

💾 Prisma ORM with transaction support for safe and consistent DB operations

🧾 Zod validation for request body and query parameters

🧠 Correlation ID tracking using AsyncLocalStorage for request tracing

📋 Winston logger with daily rotating logs and JSON formatting

💡 Modular structure following best practices for scalability

⚙️ Tech Stack
Layer   	        Technology
Language	        TypeScript
Server Framework	Express
ORM	              Prisma
Database	        MySQL
Cache & Locking	Redis + Redlock
Validation	      Zod
Logging	          Winston
Environment	      dotenv

🗂️ Project Structure
bash
Copy
Edit
src/
├── config/          # Redis, logger, env, and DB config
├── controllers/     # Business logic for APIs
├── middlewares/     # Error handling, validation, correlation ID
├── routers/         # Routes for APIs
├── utils/           # Helpers like asyncLocalStorage
├── validators/      # Zod schemas for request validation
├── server.ts        # Express app entry point
🔄 Booking Flow (with Idempotency)
Client initiates a booking request – booking details are saved, and an idempotency key is generated and returned.

Client confirms the booking by sending the idempotency key again.

Server checks if the key has been used or finalized.

If unused ➜ booking is confirmed and key is finalized.

If reused ➜ duplicate operation is avoided.

Prevents duplicate bookings caused by retries or double submissions.
