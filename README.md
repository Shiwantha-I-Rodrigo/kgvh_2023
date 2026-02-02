# Hotel Room Booking and Management System  
**King Garden View Hotel – Welimada**

## Description
This project is a web-based **Hotel Room Booking and Management System** developed as my **final year university individual project**.  
The system is designed to automate and manage hotel room reservations while supporting internal hotel operations such as user management, billing and business reporting.

The application consists of two main components:
1. **Client Portal**
2. **Management Portal**

The system was developed using **PHP**, **Lighttpd** and **MariaDB**, following standard software engineering and web security practices.

---

### Client Side (Guest)
- User registration and login.
- Secure authentication and session handling.
- Searching available rooms.
- Booking hotel rooms.
- View, update, and cancel reservations.
- Manage personal user profile.
- View booking history.
- Chat system to communicate with hotel staff.
- Password recovery with email verification.
- **Realtime** input validation.

> Home Screen

![home](/Screenshots/home.png)

> Welcome Screen

![home](/Screenshots/welcome.png)

> Registration Form

![home](/Screenshots/registration.png)

> Login Page

![home](/Screenshots/login.png)

> Room Selection

![home](/Screenshots/rooms.png)

> Reservation Confirmation

![home](/Screenshots/rooms_2.png)

> Dashboard

![home](/Screenshots/profile.png)

> Chat Feature

![home](/Screenshots/chat.png)

---

### Management Side (Admin & Staff)
- User account management.
- Room management.
- Reservation management.
- Amenities management.
- Billing and invoice handling.
- Monitoring customer communications.
- Generating business reports such as:
    + Reservation summaries
    + Revenue reports
    + Room occupancy reports

> Employee Home Screen

![home](/Screenshots/e_home.png)

> Employee Login Page

![home](/Screenshots/e_login.png)

> Employee Dashboard

![home](/Screenshots/e_profile.png)

> Employee Registration

![home](/Screenshots/e_employee.png)

> Asset Management

![home](/Screenshots/e_room.png)

> Report Generation

![home](/Screenshots/e_report.png)

---

## Technologies Used
- **Programming Language:** PHP
- **Web Server:** Lighttpd
- **Database Management System:** MariaDB
- **Frontend Technologies:** HTML, CSS, JavaScript
- **External Libraries:** PHPMailer, Bootstrap5, Jquery3, AweetAlert2
- **Operating System:** Arch Linux

---

## Security Features
- Password hashing for secure credential storage
- Session-based authentication
- Role-based access control
- Email verification for password reset
- Input validation and protection against common web vulnerabilities

---

## Installation and Configuration

1. Clone the repository:
```
git clone https://github.com/Shiwantha-I-Rodrigo/kgvh_2023.git
```

2. Database Setup:

    * Create a MariaDB database.
    * Use queries given in info.txt to setup the required DB schema.
    * Update database connection settings in the configuration file to match your DB.

3. Email Configuration:

    * Configure email settings in config.php (ie.'app password').

4. Web Server Configuration:

+ install web servers
```
    sudo pacman -S mariadb lighttpd fcgi php php-cgi
    sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
```

+ configure php-cgi
```
sudo cp /usr/share/doc/lighttpd/config/conf.d/fastcgi.conf /etc/lighttpd/conf.d/fastcgi.conf

----------------------------------------------------------------/etc/lighttpd/conf.d/fastcgi.conf

    server.modules += ("mod_fastcgi")

    index-file.names += ("index.php")
    fastcgi.server = ( 
        # Load-balance requests for this path...
        ".php" => (
            # ... among the following FastCGI servers. The string naming each
            # server is just a label used in the logs to identify the server.
            "localhost" => ( 
                "bin-path" => "/usr/bin/php-cgi",
                "socket" => "/tmp/php-fastcgi.sock",
                # breaks SCRIPT_FILENAME in a way that PHP can extract PATH_INFO
                # from it 
                "broken-scriptfilename" => "enable",
                # Launch (max-procs + (max-procs * PHP_FCGI_CHILDREN)) procs, where
                # max-procs are "watchers" and the rest are "workers". See:
                # https://wiki.lighttpd.net/frequentlyaskedquestions#How-many-php-CGI-processes-will-lighttpd-spawn 
                "max-procs" => "4", # default value
                "bin-environment" => (
                    "PHP_FCGI_CHILDREN" => "1" # default value
                )
            )
        )   
    )
----------------------------------------------------------------

----------------------------------------------------------------/etc/lighttpd/lighttpd.conf

    include "conf.d/fastcgi.conf"

----------------------------------------------------------------
```

+ locate php.ini
```
php --ini
```

+ enable extentions & enable file uploads
```
# uncomment required extention lines
extension=mysqli
file_uploads = On
```

+ start web servers
```
sudo systemctl start mariadb.service
sudo systemctl start lighttpd.service
```

---

## Limitations

* Online payment gateway is not implemented.
* SMS notifications are not supported.

---

## Planned Enhancements

+ Integration of online payment systems
+ Mobile-responsive interface improvements
+ SMS and push notification support

---

## Academic Declaration

This project was developed as part of the **final year requirements** for the University of Colombo School of Computing : Bachelor of Information technology degree program.
All work presented in this repository is original and created for academic purposes.

---

## Author

**Student Name:** WITHARANAGE SHIWANTHA INDUNIL RODRIGO\
**Institution:** UNIVERSITY OF COLOMBO SCHOOL OF COMPUTING\
**Academic Year:** 2024

---

## License

Copyright 2026 Shiwantha-I-Rodrigo

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---