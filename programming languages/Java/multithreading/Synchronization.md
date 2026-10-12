
```java
class Account { // the 'monitor'
	int balance;
	// if 'synchronized' is removed, the outcome is unpredictable
	public synchronized void deposit( ) {
	// METHOD BODY : balance += deposit_amount;
	}
	public synchronized void withdraw( ) {
	// METHOD BODY: balance -= deposit_amount;
	}
	public synchronized void enquire( ) {
	// METHOD BODY: display balance.
	}
}
```

- synchronization is needed when accessing shared resources to prevent race conditions
