# Security

[1] https://www.youtube.com/watch?v=BXRnc4o2o6E  
https://www.youtube.com/watch?v=YrqyfV8rgmI  
https://infosec.mozilla.org/guidelines/web_security  

https://crackstation.net/hashing-security.htm  
>Hash passwords with unique salts. Save the hash along with the salt. Don't use MD5 or SHA1. Use libraries and don't roll your own algorithms. Use constant time password comparison functions to avoid timing attacks.
>
>To Store a Password
>  1. Generate a long random salt using a CSPRNG.
>  2. Prepend the salt to the password and hash it with a standard password hashing function like Argon2, bcrypt, scrypt, or PBKDF2.
>  3. Save both the salt and the hash in the user's database record.  
>
>To Validate a Password
>  1. Retrieve the user's salt and hash from the database.
>  2. Prepend the salt to the given password and hash it using the same hash function.
>  3. Compare the hash of the given password with the hash from the database. If they match, the password is correct. Otherwise, the password is incorrect.
>
>Research topic: Keyed Hashes  

Certificate Pinning:  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Public_Key_Pinning  

## Multi-Factor Authentication
  
SMS:  
Social engineering.  
Someone calling the help-desk or PHONE COMPANY saying they lost their phone and register new phone number.  
Two-factor SMS gets sent to the new phone number -> hacked!
[1] 27:30

Applications:  
Duo, Authy, HDE OTP, Google Authenticator  
Better than SMS, as it is locked to the phone and not a phone number. [1] 28:00  
TODO: Research those application  

## Very insightful

https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5  
https://hackernoon.com/part-2-how-to-stop-me-harvesting-credit-card-numbers-and-passwords-from-your-site-844f739659b9
>Malicious JavaScript code running on your website from some NPM package.  
>Render sensitive information and user forms in static HTML without using any JavaScript or CSS and display it in a secure iframe on your website. Zero JavaScript goodness! Also crank your Content-Security-Policy way up!  
>X-DNS-Prefetch-Control: off  
>CSP report-uri deprecated.  
>Report-to will probably supersede report-uri.  

https://thumbsroll.blogspot.co.at/2018/01/oneplus-confirms-up-to-40000-customers.html  
https://forums.oneplus.net/threads/jan-19-update-an-update-on-credit-card-security.752415/
>Credit card number theft through XSS

https://donatstudios.com/GithubsTotalSecurityFacepalm
>Once deleted usernames should be banned from being used/created again. Keep them in the database, mark them as deleted.  
 
https://www.b-list.org/weblog/2018/feb/11/usernames/  
>User names should probably be only ASCII without whitespace for easy uniqueness (a-z, A-Z, 0-9).

https://github.com/maxchehab/CSS-Keylogging  
https://jakearchibald.com/2018/third-party-css-is-not-safe/  
>CSS Keylogger. Don't trust external or third-party CSS for sensitive information.  
