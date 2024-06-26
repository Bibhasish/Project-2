
def create_payment_receipt(customer_name, amount_paid, payment_method):
    # Create a unique filename for each receipt based on timestamp
    filename = f"payment_receipt_{datetime.now().strftime('%Y%m%d%H%M%S')}.pdf"
    
    # Initialize the PDF document
    c = canvas.Canvas(filename, pagesize=letter)
    
    # Set up some initial positions and paddings
    y_position = 750
    x_position = 50
    line_height = 15
    
    # Set up some basic formatting
    c.setFont("Helvetica-Bold", 12)
    
    # Title
    c.drawString(x_position, y_position, "Payment Receipt")
    c.line(x_position, y_position - 5, x_position + 300, y_position - 5)
    
    # Receipt details
    y_position -= 30
    c.setFont("Helvetica", 10)
    c.drawString(x_position, y_position, f"Issued to: {customer_name}")
    y_position -= line_height
    c.drawString(x_position, y_position, f"Amount Paid: ${amount_paid:.2f}")
    y_position -= line_height
    c.drawString(x_position, y_position, f"Payment Method: {payment_method}")
    
    # Footer
    c.setFont("Helvetica", 8)
    c.drawString(x_position, 50, "Thank you for your payment.")
    
    # Save the PDF file
    c.save()
    
    print(f"Payment receipt saved as: {filename}")

# Example usage:
if __name__ == "__main__":
    customer_name = "John Doe"
    amount_paid = 150.75
    payment_method = "Credit Card"
    
    create_payment_receipt(customer_name, amount_paid, payment_method)
```

