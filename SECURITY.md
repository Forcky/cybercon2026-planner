# Security

Found a vulnerability in the planner (for example a way to inject script through a share link, or to read
someone else's plan)? Please **report it privately**:
[Report a vulnerability](https://github.com/UppyAU/cybercon2026-planner/security/advisories/new)
(GitHub private vulnerability reporting). Please don't open a public issue for security problems.

I'll acknowledge within a couple of days, and credit you in the fix unless you'd rather not be named.

## Scope

- In scope: this repo's code and the public site at https://cc26plan.nb-cs.net.
- Out of scope: the official CyberCon/AISA website, MCEC's sites, and Azure or GitHub platform issues
  (report those to their owners).

## Design notes

- Everything runs in the browser. Plans, colleagues and settings live in `localStorage`; nothing is sent to a server.
- Share links carry a plan in the URL fragment (`#s=`), which browsers don't send to the web server.
- The site is served with a strict Content-Security-Policy (hash-pinned script, no third-party scripts),
  `frame-ancestors 'none'`, HSTS and `nosniff`.
