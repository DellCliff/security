# Security

[1] https://www.youtube.com/watch?v=BXRnc4o2o6E  
https://thumbsroll.blogspot.co.at/2018/01/oneplus-confirms-up-to-40000-customers.html  
https://www.youtube.com/watch?v=YrqyfV8rgmI  
https://infosec.mozilla.org/guidelines/web_security  
https://crackstation.net/hashing-security.htm  
Research topic: Keyed Hashes  

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

Malicious JavaScript code running on your website from some NPM package.  
-> Render sensitive information and user forms in static HTML without using any JavaScript and display it in a secure iframe on your website. Zero JavaScript goodness! Also crank your Content-Security-Policy way up!  

X-DNS-Prefetch-Control: off  
report-uri  

Credit card number theft through XSS:  
https://forums.oneplus.net/threads/jan-19-update-an-update-on-credit-card-security.752415/  

Once deleted usernames should be banned from being used/created again.  
https://donatstudios.com/GithubsTotalSecurityFacepalm  

User names:  
https://www.b-list.org/weblog/2018/feb/11/usernames/  

CSS Keylogger:  
https://github.com/maxchehab/CSS-Keylogging  
