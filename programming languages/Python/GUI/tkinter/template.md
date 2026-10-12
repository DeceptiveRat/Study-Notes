- input box, output box, button

```python3
#!/bin/python3

# Import the tkinter library for creating GUIs
import tkinter as tk

# button press function
def button_pressed():
    print("Button pressed!")

# Create the main application window
root = tk.Tk()

# Set the title of the window
root.title("text to MD table")

# Set the initial size of the window (width x height)
root.geometry("500x400")

# -------------------------
# Input Text Box
# -------------------------

# Create a label to describe the input box
input_label = tk.Label(root, text="Text")
input_label.pack(pady=(10, 0))  # Add vertical spacing

# Create a multi-line text widget for input
input_text = tk.Text(root, height=5, width=60)
input_text.pack(pady=5)

# -------------------------
# Button
# -------------------------

# Create a button
# The 'command' parameter is intentionally omitted
# You can add it later when you define your own function
button = tk.Button(root, text="Process", command=button_pressed)
button.pack(pady=10)

# -------------------------
# Output Text Box
# -------------------------

# Create a label to describe the output box
output_label = tk.Label(root, text="MD table")
output_label.pack(pady=(10, 0))

# Create a multi-line text widget for output
output_text = tk.Text(root, height=5, width=60)
output_text.pack(pady=5)

# -------------------------
# Start the GUI event loop
# -------------------------

# This line keeps the window open and responsive
root.mainloop()
```
