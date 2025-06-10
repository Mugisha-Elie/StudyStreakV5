# 📚 StudyStreak

**StudyStreak** is a web application designed to help students stay productive by allowing them to upload study-related files, track their progress, and manage their streaks. This project is built using HTML, CSS (Bootstrap), PHP, and MySQL.



## 🚀 Features

- 🔐 User Authentication (Sign Up, Login, Logout)
- 📁 File Upload System with:
  - Title and Description fields
  - Storage on the server
  - File path saved in the database
- 📜 View Upload History:
  - See list of uploaded files
  - Download or delete your own files
- 🔄 Session-based Access:
  - Each user sees only their files
  - Secure file handling
- 🔒 .htaccess protection on uploads folder (in progress)
- ✅ Backend and frontend separation



## 🛠️ Tech Stack

- Frontend: HTML,TailwindCss, JavaScript
- Backend: PHP (Vanilla)
- Database: Mysql
- server: Apache (XAMPP/Localhost)


---

## 🧠 Database Schema

### `users` table:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fullname VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    last_upload_date date,
    current_streak int default 0,
    longest_streak int default 0,
    profile_pic varchar(255)
);

```
### `Uploads` table
```sql
CREATE TABLE uploads (
    upload_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    name VARCHAR(255),
    title VARCHAR(255),
    description TEXT,
    file_path VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

```


---



## ✅ How It Works
1. User Creates an account
   - provides their fulllname , email and creates a password
   - their information is saved to the database and also a session is created basing on the id they are assigned from the database and their fullname,
     this is to separate their log in sessions from other users
   - After the user creates an account their streak is currently 0
  
2. File Upload
   - Only logged in users can access the upload page
   - A user enters a title, description, and uploads a file(optional)
   - The file is then stored on the uploads folder and the path is stored to the database
   - In the uploads table the filepath is stored linked to the user_id foreign key that points to the user's id who uploaded it

3. View History
   - A logged in user can also view their own history because it is retrieved basing on the user id for the current session
      - A user can view their history, download the file it was uploaded
      - A user can also delete the file from the history and it is also deleted from the server

4. Profile Picture
   - A logged in user can set their profile picture

5. Logout and Account Delete
   - A logged in user have the option to opt out or even permanently delete their account from the application
  



## The END


## Contributors: - Allan MUTABAZI  | IRADUKUNDA Mugisha Elie
                 


![Thank You](https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif)





