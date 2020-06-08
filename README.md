# SMTP_PyPi_Package
 - SMTP Helper functions. Only uses Standard Library. 
 
#### email_without_attachment: Send email without attachments.
```python

def email_without_attachment(message: str, subject: str, to_list: str, cc_list: str, login: str, password: str):
    """
    :param message: HTML String with Email message contained. See Examples/Email_Strings.py
    :param subject: Subject String
    :param to_list: Semicolon separated list of email addresses. (ex - a@abc.com; b@abc.com; c@abc.com;)
    :param cc_list: Semicolon separated list of email addresses. (ex - a@abc.com; b@abc.com; c@abc.com;)
    :param login: Login email. 
    :param password: Password for O365
    """
```
##### Example Call 
```python
from mj.smtputility import email_without_attachment
test_message = """
<HTML>
    <BODY>
     Message Text
     <br>
    </BODY>
</HTML>
"""

smtp_msg_automation.email_without_attachment(test_message,'SMTP Testing','a@abc.com;b@abc.com;','c@abc.com','email@domain.com','password')

```

#### email_with_attachments: Send email with attachments. Can send any number/type of attachments in email. 
```python

def email_with_attachments(
        message: str, subject: str, to_list: str, cc_list: str, login: str, password: str, *args
):
    """ 
        :param login: Login email. 
        :param password: Password for O365.
        :param message: HTML String with Email message contained. See Examples/Email_Body.html.
        :param subject: Subject String
        :param to_list: Semicolon separated list of email addresses. (ex - a@abc.com; b@abc.com; c@abc.com;)
        :param cc_list: Semicolon separated list of email addresses. (ex - a@abc.com; b@abc.com; c@abc.com;)
        :param *args: Paths to attachments. 
        """
```
##### Example Call 
```python
from mj.smtputility import email_with_attachments
import smtp_msg_automation
test_message = """
<HTML>
    <BODY>
     Message Text
     <br>
    </BODY>
</HTML>
"""

smtp_msg_automation.email_with_attachments(test_message,'SMTP Testing','a@abc.com;b@abc.com;','c@abc.com','email@domain.com','password',
r'C:\Users\user\some_directory\test_1.txt')
```

#### notify_error: Automated email report for use in exception catch. 
```python
def notify_error(report_name, error_log, to_list: str,login: str, password: str):
    """

    :param to_list: List of emails to receive notification.
    :param report_name: Name of automated report.
    :param error_log: Raised exception or other error to report.
    :param login: Login email. 
    :param password: Password for O365
    """
```
##### Example Call
```python
from mj.smtputility import notify_error
import os
def foo():
    #do thing
try:
    foo()
except Exception as e:
    smtp_msg_automation.notify_error(f"{os.path.basename(__file__)}", e, "a@email.com",'email@domain.com','password')
```