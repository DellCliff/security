# Security

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
>Difficult to get right and high risk to screw up.

## Multi-Factor Authentication

[1] https://www.youtube.com/watch?v=BXRnc4o2o6E  
>SMS:  
>Social engineering.  
>Someone calling the help-desk or PHONE COMPANY saying they lost their phone and register new phone number.  
>Two-factor SMS gets sent to the new phone number -> hacked! [1] 27:30

>Applications:  
>Duo, Authy, HDE OTP, Google Authenticator  
>Better than SMS, as it is locked to the phone and not a phone number. [1] 28:00  
>TODO: Research those application  

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

## HTTP-Headers
Referrer-Policy: no-referrer  
>The Referer header will be omitted entirely. No referrer information is sent along with requests.  

Strict-Transport-Security: max-age=63072000; includeSubDomains  
>HSTS. The first time your site is accessed using HTTPS and it returns the Strict-Transport-Security header, the browser records this information, so that future attempts to load the site using HTTP will automatically use HTTPS instead.  

X-Content-Type-Options: nosniff  
>This header was introduced by Microsoft in IE 8 as a way for webmasters to block content sniffing that was happening and could transform non-executable MIME types into executable MIME types. Since then, other browsers have introduced it, even if their MIME sniffing algorithms were less aggressive.  

X-Frame-Options: deny  
>The X-Frame-Options HTTP response header can be used to indicate whether or not a browser should be allowed to render a page in a <frame\>, <iframe\> or <object\> . Sites can use this to avoid clickjacking attacks, by ensuring that their content is not embedded into other sites.  

X-Permitted-Cross-Domain-Policies: none  
>A cross-domain policy file is an XML document that grants a web client, such as Adobe Flash Player or Adobe Acrobat (though not necessarily limited to these), permission to handle data across domains. When clients request content hosted on a particular source domain and that content make requests directed towards a domain other than its own, the remote domain needs to host a cross-domain policy file that grants access to the source domain, allowing the client to continue the transaction. Normally a meta-policy is declared in the master policy file, but for those who can’t write to the root directory, they can also declare a meta-policy using the X-Permitted-Cross-Domain-Policies HTTP response header.  

X-XSS-Protection: 1; mode=block  
>X-XSS-Protection is a feature of Internet Explorer and Chrome that stops pages from loading when they detect reflected cross-site scripting (XSS) attacks. Although these protections are largely unnecessary in modern browsers when sites implement a strong Content Security Policy that disables the use of inline JavaScript ('unsafe-inline'), they can still provide protections for users of older web browsers that don’t yet support CSP.

Content-Security-Policy 

## CSRF
1. Same Origin Checks
    1. Source Origin Checks
        * Origin Header Check
        * Referer Header Check
        >Both of these headers can be spoofed of course, although not by JS (XSS attacks) since they are on the forbidden headers list, and can only be set by the browser itself.
    2. Target Origin Checks
        * Predefined value
        * Host Header Check
        * X-Forwarded-Host Header Check
    3. Compare Source Origin with Target Origin
2. CSRF-Token
    * Unique per user session
    * Large random value
    * Generated by a cryptographically secure random number generator
    * The CSRF token is added as a hidden field for forms or within the URL if the state changing operation occurs via a GET
    * Any state changing operation requires a secure random token (e.g., CSRF token) to prevent CSRF attacks
