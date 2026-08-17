# experiment2
this was example of payment interface code

# Strategy Pattern Example
# -----------------------------

# Parent Class (Base Strategy)
class PaymentStrategy:

    # Method to be implemented by child classes
    def pay(self, amount):
        pass


# Credit Card Strategy
class CreditCardPayment(PaymentStrategy):

    # Override the parent method
    def pay(self, amount):
        print(f"Payment of ₹{amount} made using Credit Card")


# PayPal Strategy
class PayPalPayment(PaymentStrategy):

    # Override the parent method
    def pay(self, amount):
        print(f"Payment of ₹{amount} made using PayPal")


# UPI Strategy
class UPIPayment(PaymentStrategy):

    # Override the parent method
    def pay(self, amount):
        print(f"Payment of ₹{amount} made using UPI")


# Context Class
class PaymentContext:

    # Constructor
    def _init_(self, strategy):
        self.strategy = strategy

    # Change payment method
    def set_strategy(self, strategy):
        self.strategy = strategy

    # Perform payment
    def make_payment(self, amount):
        self.strategy.pay(amount)


# -----------------------------
# Main Program
# -----------------------------

# Create Credit Card Strategy
credit = CreditCardPayment()

# Pass strategy to context
payment = PaymentContext(credit)

# Make first payment
payment.make_payment(1000)

# Change strategy to PayPal
paypal = PayPalPayment()
payment.set_strategy(paypal)

# Make second payment
payment.make_payment(500)

# Change strategy to UPI
upi = UPIPayment()
payment.set_strategy(upi)

# Make third payment
payment.make_payment(750)
