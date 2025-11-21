1. Price Manipulation

Change price with another value

100 → 50

Change price to a negative value

100 → -100

Add negative value to manipulate total

100 → (+-120)

Multiply price by a decimal

100 → 0.5 × 100

2. ID / Profile Enumeration & Authorization Bypass

Change user ID to another predictable value to retrieve another profile

1001 → 1089

3. Shopping Cart Bypass

Bypass authentication to access checkout/payment flow directly.

4. Review Functionality Abuse

Post verified reviews without purchase

Submit rating outside allowed range (0, 6, -1)

Post multiple ratings (Race Condition)

Upload unsupported file extensions

Post reviews as another user

Test CSRF on review endpoints

5. Coupon Code Functionality

Reuse coupon more than once

Race condition using one coupon for two accounts

Try HPP or Mass Assignment to add multiple coupon codes

Test for input sanitization issues (XSS/SQLi)

Apply coupon on products not eligible

6. Delivery Charges Abuse

Change delivery fee to negative value

Modify params to get free delivery

7. Currency Arbitrage

Pay in currency A and request refund in currency B

8. Premium Feature Abuse

Access premium-only endpoints without upgrade

Use premium features after refund

Modify true/false premium access flags

Replace premium validation values via Burp

Check cookies/local storage for premium access flags

9. Refund Feature Abuse

Refund after purchase while still accessing the service

Try currency arbitrage via refunds

Trigger multiple refunds via race condition

10. Cart / Wishlist Abuse

Add negative quantity items

Add more than available stock

Move wishlist items to others’ carts / modify other users’ lists

11. Thread Comment Functionality

Unlimited comments

Post multiple comments using race condition

Post verified/privileged comments without permission

Post as another user

12. Parameter Tampering

Manipulate payment/critical fields

Add unexpected fields via HPP or Mass Assignment

Response manipulation (e.g., 2FA bypass)

13. Parameter Tampering → Price Manipulation

Reference material:
https://www.youtube.com/watch?v=3VMlV7j_yzg

14. Exam Result Manipulation (Semrush Example)

Modify JSON answers (1 = true, "" = false) to pass exam

15. Authentication Flags & Privilege Escalation

Identify permission flags

Modify values (1→0 / Y→N)

Fuzz ACL-related parameters

16. Critical Parameter Manipulation

Look for predictable/incrementing parameters

Change values to gain unauthorized access

17. Cookie Tampering

Identify developer-defined cookies

Look for predictable numeric values

Modify cookies to escalate privileges

18. LDAP Parameter Abuse

Identify LDAP-related parameters

Inject LDAP filters: *, OR, AND

Escalate authorization via LDAP bypass

19. Business Constraint Exploitation

Identify parameters defining business rules (limit, max, transfer amount)

Modify hidden values to bypass constraints

20. Business Flow Bypass

Skip required steps (e.g., checkout → payment → confirmation)

Tamper with hidden step parameters

21. Identity / Profile Extraction

Identify session tokens / user identifiers

Guess or reverse engineer token to access other accounts

22. File / URL Access & Information Leakage

Identify file-related parameters (file/doc/dir)

Fetch other users’ files directly via URL manipulation

23. Null Payloads

Test sending null, empty, "", or no-value fields

24. Change Password Abuse

Delete the "current password" field to bypass validation
