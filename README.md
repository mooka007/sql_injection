# sql_injection
SQL injection is a type of injection attack. Injection attacks occur when maliciously crafted inputs are submitted by an attacker, causing an application to perform an unintended action. Because of the ubiquity of SQL databases, SQL injection is one of the most common types of attack on the internet.

If you only have time to protect yourself against one vulnerability, you should be checking for SQL injection vulnerabilities in your codebase!

## risks
What’s the worst thing that could happen when you suffer a SQL injection attack?

Our example hack showed you how to bypass the login page: a huge security flaw for a banking site. More complex attacks will allow an attacker to run arbitrary statements on the database. In the past, hackers have used injection attacks to:

Extract sensitive information, like Social Security numbers, or credit card details.
Enumerate the authentication details of users registered on a website, so these logins can be used in attacks on other sites.
Delete data or drop tables, corrupting the database, and making the website unusable.
Inject further malicious code to be executed when users visit the site.
SQL injection attacks are astonishingly common. Major companies like Yahoo and Sony have had their applications compromised. In other cases, hacker groups targeted specific applications or wrote scripts intended to harvest authentication details. Not even security firms are immune!

## protection

So SQL Injection is a serious risk. How can you protect yourself?

Parameterized Statements
Programming languages talk to SQL databases using database drivers. A driver allows an application to construct and run SQL statements against a database, extracting and manipulating data as needed. Parameterized statements make sure that the parameters (i.e. inputs) passed into SQL statements are treated in a safe manner.

For example, a secure way of running a SQL query in JDBC using a parameterized statement would be:
```
// Connect to the database.
Connection conn = DriverManager.getConnection(URL, USER, PASS);

// Construct the SQL statement we want to run, specifying the parameter.
String sql = "SELECT * FROM users WHERE email = ?";

// Generate a prepared statement with the placeholder parameter.
PreparedStatement stmt = conn.prepareStatement(sql);

// Bind email value into the statement at parameter index 1.
stmt.setString(1, email);

// Run the query...
ResultSet results = stmt.executeQuery(sql);

while (results.next())
{
    // ...do something with the data returned.
}
```
