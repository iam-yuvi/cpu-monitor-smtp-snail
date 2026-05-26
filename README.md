## CPU Monitor with Email Alert

This project includes a Bash script that monitors CPU usage on a Linux system.
If CPU usage goes above 50%, it sends an alert email using Gmail SMTP.

### Files:
- cpu_monitor.sh       → Script that checks CPU usage and sends email
- s-nail.rc            → Email configuration for Gmail SMTP
- cronjob.txt          → Cron job to run the script every minute

### Setup Steps:
1. Install required packages:
```bash
   yum install s-nail bc -y
```
2. Edit s-nail.rc and configure it like this:
```text
   set mta="smtp://smtp.gmail.com:587"
   set smtp-use-starttls
   set smtp-auth=login
   set smtp-auth-user="your_email@gmail.com"
   set smtp-auth-password="your_app_password"
   set from="your_email@gmail.com"
```
3. Add this line to your crontab:
```bash
   * * * * * /full/path/to/cpu_monitor.sh >> /var/log/cpu_monitor.log 2>&1
```

### Notes:
- Make sure to use a Gmail app password, not your actual Gmail password.
- The script uses 'bc' to handle decimal math.
- s-nail sends the email using the configured SMTP settings.
