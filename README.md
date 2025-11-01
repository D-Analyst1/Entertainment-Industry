# 🎬 Entertainment Streaming Analytics (SQL Project)

<img width="300" height="168" alt="image" src="https://github.com/user-attachments/assets/deb71b47-32fe-4257-a489-dcaf9dc728fc" />


## 📖 Project Overview
This project analyzes a simulated **entertainment streaming platform** dataset using **pure SQL**.  
It focuses on user engagement, content performance, and revenue trends — the kind of insights real streaming companies (like Netflix, Spotify, or Showmax) rely on for decision-making.

All analysis was performed **entirely in SQL**, without using visualization tools.

---

## 🗂️ Database Structure

The project consists of **five main tables**:

| Table Name | Description |
|-------------|-------------|
| **Users** | Contains user demographics and subscription information |
| **Content** | Details about movies, series, and music (genre, duration, release year, etc.) |
| **Streams** | Records each streaming session (user, content, date, and watch time) |
| **Ratings** | Stores user ratings and feedback per content |
| **Payments** | Tracks payment amounts, methods, and subscription renewals |

---

## 🎯 Project Objectives

The SQL analysis was designed to answer the following key business questions:

1. Who are the most active users on the platform?
2. Which countries have the highest streaming activity?
3. What genres and content categories perform best?
4. Which subscription types generate the most revenue?
5. What is the watch-time behavior across months?
6. Which users are at risk of becoming inactive?
7. How do ratings correlate with content performance?

---

## 🧰 SQL Techniques Used

- **JOINs** (INNER, LEFT) for combining relational tables  
- **Aggregate functions**: `SUM()`, `AVG()`, `COUNT()`  
- **Date functions**: `YEAR()`, `DATENAME()`, `DATEDIFF()`  
- **CASE statements** for classifying ratings  
- **CTEs & Window functions**: `RANK()` for ranking genres  
- **ALTER & UPDATE** for column manipulation and data cleaning  

---

## 🧮 Key Insights

| Insight | Summary |
|----------|----------|
| 🌍 **Active Countries** | Nigeria and South Africa led in total streaming hours |
| 👥 **Most Engaged Users** | Premium users recorded the highest total watch time |
| 🎶 **Top Genres** | Afrobeat and Drama dominated total streams |
| 💳 **Revenue Drivers** | Premium subscriptions contributed the most revenue |
| ⏰ **Inactive Users** | Free users had the longest inactivity periods |
| ⭐ **Content Ratings** | “Soft Life” and “Lost in Lagos” were among the highest-rated titles |

---

## 🧾 Sample SQL Queries

### 1️⃣ Most Active Users
```sql
SELECT 
    u.Name,
    u.Country,
    u.SubscriptionType,
    SUM(s.WatchTime) AS TotalWatchTime
FROM Streams s
JOIN Users u ON s.UserID = u.UserID
GROUP BY u.Name, u.Country, u.SubscriptionType
ORDER BY TotalWatchTime DESC;



