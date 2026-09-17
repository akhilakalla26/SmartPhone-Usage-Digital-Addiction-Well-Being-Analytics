# 📱 Smartphone Usage & Addiction Analysis

This project uses **MySQL** to study how daily screen time (social media, gaming) affects sleep, stress levels, and mobile phone addiction.

---

## 📊 Dataset Columns

The database table `smartphone_usage` contains the following details:

* **User:** `user_id`, `age`, `gender`
* **Habits:** `daily_screen_time_hours`, `social_media_hours`, `gaming_hours`, `weekend_screen_time`
* **Activity:** `notifications_per_day`, `app_opens_per_day`
* **Impact:** `sleep_hours`, `stress_level`, `academic_work_impact`
* **Status:** `addiction_level`, `addicted_label` (0 = No, 1 = Yes)

---

## 🖥️ Interactive Dashboard

The repository includes a ready-to-use Power BI dashboard template (located in the `/Report` folder) to visualize these trends instantly.

### Key Charts Included:
* **Addiction Levels:** A breakdown of users from None to Severe risk.
* **Habit Tracking:** Comparison of sleep hours vs. average daily screen time.
* **Stress Indicators:** Live look at how daily notification volume triggers high stress.

To open it, launch Power BI Desktop and open the file located at `Report/definition/report.json`.

---

## 🔍 Core SQL Queries

### 1. Addiction Count by Gender
```sql
SELECT gender, COUNT(*), SUM(CASE WHEN addicted_label = 1 THEN 1 ELSE 0 END) AS addicted_count 
FROM smartphone_usage 
GROUP BY gender;
```

### 2. Average Usage & High Stress Rate
```sql
SELECT AVG(daily_screen_time_hours), AVG(sleep_hours), AVG(stress_level = 'High') 
FROM smartphone_usage;
```

### 3. Impact on Work and Studies
```sql
SELECT academic_work_impact, AVG(daily_screen_time_hours), AVG(social_media_hours), AVG(gaming_hours) 
FROM smartphone_usage 
GROUP BY academic_work_impact;
```

---

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   ```

2. **Set up MySQL:**
   ```sql
   CREATE DATABASE smartphone;
   USE smartphone;
   ```

3. **Run your scripts:** Import the dataset into your database tool, connect it to your dashboard, and execute the queries above to see the results.
