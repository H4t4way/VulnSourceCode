# Find Vulns on Java Platforms 
## Small Legenda of Functions that you must check during code review


![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)

In this session you will see the most common JAVA functions, potentially dangerous APIs and
security configurations.

- Type some Markdown on the left
- See HTML in the right
- ✨JAVA the Best ✨

## APIs used to aquire data from the user 


- All this APIs  are used in GET and POST request, stored as a String value. Every time on the code make some kind of grep of these APIs, you can find really juicy things.!
- <font color="green"> getParameter</font> 
- <font color="green"> getParamaterNames</font>      
- <font color="green"> getParameterValues</font>
- <font color="green"> getParameterMap</font>

Can you spot the correct code and the wrong one?
Example of wrong code that lead to Cross Site Scripting XSS.

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws IOException {
  String name = req.getParameter("Ginoparam");
  PrintWriter out = resp.getWriter();
  out.write("Hello " + Ginoparam);

```

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws IOException {
  String name = req.getParameter("Ginoparam");
  String encodedName = org.owasp.encoder.Encode.forHtml(name);
  PrintWriter out = resp.getWriter();
  out.write("Hello " + encodedName);
}
```
-----------------

As we can see the parameter 'ginoparam' in the first code is not sanitized, a malicious attacker can inject javascript code on 'ginoparam' and XSS will be triggered  out.

- <font color="green"> getQueryString</font> 
- Retire the entire query string and could be used instead <font color="green"> getParameter</font> 
-----------------

- <font color="green"> getHeader</font> 
- <font color="green"> getHeaders</font>      
- <font color="green"> getHeadersNames</font>
- All the HTTP headers stored in the request are stored as string and can be accessed with these APIs.
-----------------

- <font color="green"> getRequestURI</font> 
- <font color="green"> getRequestURL</font>      
- Giving back all the url request with also all the query string.
-----------------



> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.






















[http://h4t4way.root.sx](http://h4t4way.root.sx/)

## License

H4t4way

