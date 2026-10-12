
```python
#!/bin/python3 

import tkinter as tk
from tkinter import scrolledtext

def defang():
    text = input_box.get("1.0", tk.END).strip()
    # Basic defanging rules
    text = text.replace(".", "[.]").replace("http", "hxxp")
    output_box.delete("1.0", tk.END)
    output_box.insert(tk.END, text)

# Main window
root = tk.Tk()
root.title("Defanger Tool")
root.geometry("600x400")

# Input label and box
tk.Label(root, text="Input:").pack(anchor="w", padx=10, pady=(10, 0))
input_box = scrolledtext.ScrolledText(root, wrap=tk.WORD, height=8)
input_box.pack(fill="both", expand=True, padx=10, pady=5)

# Defang button
tk.Button(root, text="Defang", command=defang).pack(pady=5)

# Output label and box
tk.Label(root, text="Output:").pack(anchor="w", padx=10)
output_box = scrolledtext.ScrolledText(root, wrap=tk.WORD, height=8)
output_box.pack(fill="both", expand=True, padx=10, pady=(0, 10))

root.mainloop()
```
