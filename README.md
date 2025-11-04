# 🏪 Real-Time Marketplace API (Laravel 11)

![Laravel Logo](https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg)

[![Laravel Version](https://img.shields.io/packagist/v/laravel/framework)](https://packagist.org/packages/laravel/framework)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

---

## 📖 Overview

The **Real-Time Marketplace API** is a backend-only Laravel 11 application that powers a marketplace where **buyers** can bid on and reserve listings from **sellers** — all handled safely and concurrently.

This API ensures **atomic operations**, **race-free inventory handling**, and **automatic reservation expiry** using Laravel’s built-in job queue and Redis locks (optional).

---

## ⚙️ Tech Stack

- **Backend:** Laravel 11  
- **Database:** SQLite  
- **Cache & Queue (optional):** Redis  

---

## 🧱 Architecture

| Entity | Description |
|---------|--------------|
| **User** | Core authentication entity |
| **Buyer** | Buyer profile linked to user |
| **Seller** | Seller profile linked to user |
| **Listing** | Products or services sold by sellers |
| **Availability** | Optional time slots or quantity-based availability |
| **Bid** | Buyer offers on listings |
| **Reservation** | Holds or final bookings with atomic updates |
| **AuditLog** | Optional table for tracking key actions |

---

## 🔁 Flow Summary

1. User registers and creates a **buyer** or **seller** profile  
2. **Seller** adds a listing (optionally with availability slots)  
3. **Buyer** browses listings and **places bids**  
4. **Seller** accepts or rejects bids  
5. **Buyer** creates a **reservation** (atomic hold with SQLite transaction)  
6. **Held reservations** expire automatically after 15 minutes  
7. **Buyer** confirms reservation to finalize  

---

## ⚡ Local Setup (SQLite)

### 1. Clone the repository
  - git clone https://github.com/Lambertn33/marketplace-api
### 2. Install Dependencies
  - composer install
### 3. Environment setup:
  - cp .env.example .env

### 4. Database Setup:
  - In your .env setup DB NAME PASSWORD HOST and PORT

### 5. Tables Creation
  - php artisan migrate
  - php artisan DB:seed
  - php artisan serve
  
