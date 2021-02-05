# Solution

The login form gives a hint that this challenge may be based on SQL Injection Attack. By using the a simple sqli payload like `' OR '1'=='1` in both username and password field we find that "=" is not allowed. To bypass this we can use any of the following playloads-
```
' OR '1' LIKE '1 (in both username and password)
' OR '1' LIKE '1';--  (only in the username)
' OR 1 ;-- (only in the username)  and Likewise many others
```

On getting logged in, we try to get the agent name for 'Yagami Light', but we are told that we don't have enough authority! Since we already know that the server uses SQL database, we may use the string comparison properties of SQL which are different from the programming language used in backend. SQL ignores trailing spaces in string comparison with "where" clause, but this is not the case with other programming languages. Using any such property, we can bypass the server checking for authority and still get the correct result from SQL query. Hence using `'Yagami Light '` (notice the trailing space) as the payload gets us the flag.

## Flag
```
flag:ApplesAreBest
```