You can recover user id and password from DB
---------------------------------------------
There are 3 Methods to recover wordpress admin panel

    01. In this case you must have old user id and password
    02. By changing Username and Password (Function -> MD5)
    03. Using SQL Queries

We will follow 02 and 03 options:
---------------------------------------------
Method 02. By changing Username and Password (Function -> MD5)

    Step 01. Select your DB
    Step 02. Select wp_users
    Step 03. Click on Edit button of the Existing User in line at start.
    Step 04. Update user_email and user_password
    Step 05. After changing, At bottom right corner there is a button "Go". Just click on it and save it.
    Step 06. Visit www.yoursite.com/wp-admin and enter Email and Password
    Step 07. You will be successfully logged in into the wp-admin
    Enjoy, You have done this ☺️👌

Method 03. By executing the SQL Queries (Creating New Admin User)

   Step 01. Select your DB
   Step 02. Paste this query:

    INSERT INTO wp_users 
    (user_login, user_pass, user_nicename, user_email, user_status) 
    VALUES ('sk_admin', MD5('Admin@12345'), 'sk_admin', 'your@email.com', 0);

   Step 03. Then Run:

    INSERT INTO wp_usermeta (user_id, meta_key, meta_value)
    SELECT ID, 'wp_capabilities', 'a:1:{s:13:"administrator";b:1;}'
    FROM wp_users WHERE user_login = 'sk_admin';

   Step 04. Then run:

    INSERT INTO wp_usermeta (user_id, meta_key, meta_value)
    SELECT ID, 'wp_user_level', '10'
    FROM wp_users WHERE user_login = 'sk_admin';

   Step 05. Login at the (www.yoursiteurl.com/wp-admin)
   Step 06. Enter the new credential and login

   Here you have successfully recovered you wp account ☺️👌
