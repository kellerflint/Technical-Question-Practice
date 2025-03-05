# Whiteboarding Question: Payment Processing System  

## Problem Statement  
You are designing a **payment processing system** for an online store. The store supports multiple payment methods:  
- **Credit Card**  
- **PayPal**  
- **Bitcoin**  

### **Requirements:**  
1. The checkout system must be able to **process any payment** in the same way.  
2. Each payment method must have a `process(double amount) -> boolean` function that:  
   - Takes an amount as input.  
   - Returns whether the payment was successful.  
3. Different payment methods require **different data** to be created:  
   - **PayPal** needs an **email and password**.  
   - **Credit Card** needs a **card number, CVV, and billing address**.  
   - **Bitcoin** needs a **wallet address**.  
4. The system should be **easily extendable** to support future payment methods.  

### **Example Expected Usage:**  
```java
public static void checkout(PaymentMethod paymentMethod, double amount) {
    if (paymentMethod.process(amount)) {
        System.out.println("Payment successful!");
    } else {
        System.out.println("Payment failed!");
    }
}

public static void main(String[] args) {
    PaymentMethod paypalPayment = new PayPal("user@example.com", "securepassword");
    PaymentMethod creditCardPayment = new CreditCard("1234-5678-9012-3456", "123", "123 Main St");
    PaymentMethod bitcoinPayment = new Bitcoin("1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa");

    checkout(paypalPayment, 50.00);  
    checkout(creditCardPayment, 100.00);  
    checkout(bitcoinPayment, 200.00);  
}
