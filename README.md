Requirements:
    Python 3.6+
    Kali Linux
    Hydra
    bWAPP
    Burp Suite
    ReportLab (for PDF generation)
    Local vulnerable app (bWAPP) running

--------------------------------------------------------------------------------------------------------
Usage:

Create project directory and virtual environment
    mkdir BrokenAuthDetect && cd BrokenAuthDetect
    python3 -m venv venv
    source venv/bin/activate

Install required Python packages
    pip install requests
    pip install requests reportlab

Ensure Hydra is installed and test it with:
    hydra -l bee -P passwords.txt 192.168.1.1 http-post-form "/bWAPP/login.php:login=^USER^&password=^PASS^&security_level=0&form=submit:Invalid"

Run the script
    python3 auth_tester.py

--------------------------------------------------------------------------------------------------------
About code:
    Brute-Force Testing with Hydra – Simulates login attacks using common credentials.
    Rate Limiting Evaluation – Sends multiple login attempts to check for lack of account lockout.
    Session Fixation Detection – Compares PHP session tokens before and after login.
    PDF Report Generation – Summarizes all test results in a timestamped, downloadable report.
    Burp Suite Integration – Captures live requests and structures payloads dynamically.

--------------------------------------------------------------------------------------------------------
Result:
    Brute-force attempt logs with timestamps
    Rate limiting behavior summary
    Session IDs before and after login
    Final vulnerability evaluation with pass/fail status

--------------------------------------------------------------------------------------------------------