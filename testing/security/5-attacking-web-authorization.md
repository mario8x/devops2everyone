# attacking web authorization

Authorization determine what parts of the application authenticated users can access.

* user's session, access token, access control list (ACL): upon logout or session timeout, the token is typically deleted, expired, or otherwise invalidated
* http basic authn: base64-encoded `username:password` sin http authorize header for every request

# Attack techniques

## Fingerprinting authz

seek to "fingerprint" the authz implementation first in order to get the lay of the land before launching over attacks

* Crawling ACLs :  the easiest way to check the ACLs across a site is to simply crawl it.

by using tool Offline Explorer Pro

## Identify Access Tokens

* access tokens: are often easy to see within web application flows
```
Session-Attribute   Common Abbreviation
Username            username, user, uname, customer
User Identifier     id, *id, userid, uid, *uid, customerid
User Roles          admin=TRUE/FALSE, role=admin, priv=1
User Profile        profile, prof
Shopping cart       cart, cartid
Session Identifier  session ID, sid, sessid
```

* COTS session IDs: many common off-the-shelf (COTS) web servers have the capability to generate their own pseudorandom session IDs.
```
server-type server-session-id-variable-name
  iis   ASPSESSIONID
  J2ee-based servers  JSESSIONID
  php PHPSESSIONID
  apache  SESSIONID
  Coldfusion CFID
             CFTOKEN JSESSIONID (runs on top of J2EE)
  Other Servers JServSessionID
                JWSESSIONID
                SESSID
                SESSION
                SID
                session_id
```
# Analyzing Session Tokens

* Authz attack case studies
* Authz best practices

# tools

* Offline Explorer Pro (from MetaProducts Software Corp.)
