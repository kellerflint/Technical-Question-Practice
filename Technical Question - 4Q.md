# Whiteboarding Question: Notification System  

### **Requirements:**  
Every notification must have a recipient (who receives the message).  

Each notification type must have a send() method that prints the message to the console.  

Different types of notifications have different message formats:  

An **EmailNotification** should print:  
```
Sending Email to user@example.com: "You've got mail!"
```
A **SMSNotification** should print:  
```
Sending SMS to +1234567890: "New message received!"
```
A **PushNotification** should print:  
```
Sending Push Notification to user123: "Check your app for updates!"
```

The system should be easily extendable to support more notification types in the future without modifying existing code.  

You should be able to store multiple notifications in a queue and send them all using a loop.  

---

## **Example Expected Usage**
```java
Notification email = new EmailNotification("user@example.com");
Notification sms = new SMSNotification("+1234567890");
Notification push = new PushNotification("user123");

email.send();
sms.send();
push.send();
```
```
Sending Email to user@example.com: "You've got mail!"
Sending SMS to +1234567890: "New message received!"
Sending Push Notification to user123: "Check your app for updates!"
```

## Task
- Design and implement the Notification structure so that all notifications can be handled in the same way.
- Ensure that new notification types can be added without modifying existing code.
- Implement a function that takes a list of notifications and calls send() on each of them.
