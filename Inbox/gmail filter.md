

16-10-2025 17:30

Status: #in_progress

Tags:

# gmail filter
## built-in search filters
``` gmail
has:attachment larger:1mb older_than:1y 
# or
before:2024/01/01
# or
has:attachment filename:(pdf OR zip OR docx) larger:15M older_than:18m
```

## Use Gmail “Storage Management” tool
https://one.google.com/storage/management

## Google Apps Script
1. https://script.google.com
2. New Project
3. delete the default code and paste this:
``` javascript
function listLargeOldEmails() {
  // finds emails older than 1 year with attachments larger than 10 MB
  var threads = GmailApp.search('has:attachment larger:10M older_than:1y');
  Logger.log("Found " + threads.length + " threads");

  for (var i = 0; i < threads.length; i++) {
    var messages = threads[i].getMessages();
    for (var j = 0; j < messages.length; j++) {
      var msg = messages[j];
      Logger.log(
        "From: " + msg.getFrom() +
        " | Subject: " + msg.getSubject() +
        " | Date: " + msg.getDate()
      );
    }
  }
}

```
4. save
5. run
6. view logs

## My Questions


## References



