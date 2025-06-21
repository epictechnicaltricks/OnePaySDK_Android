# 📦 SDK Notice
🛠️ Reworked by: Shubhamjit
📧 Contact: subhamjeetdash2002@gmail.com

Last modified in June 2025. Check the official website for the latest version and modification details.

Official Integration URL: https://www.1pay.in/integrations.php
Official Website : https://www.1pay.in/ 

This SDK was completely restructured by Shubhamjit due to the poor coding standards in the original version. It is now rebuilt to be clean, efficient, and as easy to integrate as other modern SDKs.
The focus was on improving maintainability, readability, and integration speed without compromising functionality.


# OnePay Payment Gateway Integration for Android

A complete implementation of the OnePay payment gateway in Android applications, supporting both Activity and Fragment implementations with proper callback handling.

## Features

- Seamless integration with OnePay payment gateway
- Support for both Activity and Fragment implementations
- Comprehensive payment status callbacks (Success, Failed, Timeout, Pending)
- Sample implementation with best practices
- Secure transaction handling
- Debug mode support for testing

## Prerequisites

- Android Studio (latest version)
- Android SDK 21+
- OnePay merchant account
- OnePay Android SDK (`onepay-pg-lib`)

## Installation

1. Add the OnePay library to your project:

Here’s the corrected version:

**"Unzip it, then place the SDK outside the *app* directory and follow the instructions."**

```settings.gradle or settings.gradle.kts

include ':onepay-pg-lib' on settings.gradle

```

```gradle

implementation project(path: ':onepay-pg-lib')

```

Implementation Guide
Basic Setup
Implement the OnePayPaymentStatus interface in your Activity or Fragment:


```kotlin
class PaymentActivity : AppCompatActivity(), OnePayPaymentStatus {
    // Implement callback methods
    override fun onePayPayment_Success(response: PaymentResponse?) { ... }
    override fun onePayPayment_Failed(response: PaymentResponse?) { ... }
    // ... other callbacks
}
```

Initiating Payment

```kotlin
private fun initiatePayment() {
    val paymentRequest = PaymentRequest(
        merchantId = "YOUR_MERCHANT_ID",
        transactionId = generateUniqueTransactionId(),
        reqData = "YOUR_PAYMENT_DATA",
        isDebug = BuildConfig.DEBUG
    )
    
    OnePayCheckout().startPayment(paymentRequest, this)
}
```


Handling Callbacks

kotlin
```override fun onePayPayment_Success(response: PaymentResponse?) {
    runOnUiThread {
        // Update UI and show success message
        showPaymentStatus("Payment Successful", true)
        Log.d("Payment", "Transaction ID: ${response?.transactionId}")
    }
}

```
Configuration
Parameter	Description	Required

```
merchantId	>> Your OnePay merchant ID	Yes
transactionId	>> Unique transaction identifier	Yes
reqData >>	Payment request data (JSON)	Yes
isDebug >>	Enable/disable debug mode	Yes
```



__________________________________
