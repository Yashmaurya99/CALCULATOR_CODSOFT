# CALCULATOR_CODSOFT
# Simple Python Calculator

This is a basic calculator implemented in Python using the Tkinter library for the graphical user interface.

## How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/calculator-python.git
   ```

2. Navigate to the project directory:

   ```bash
   cd calculator-python
   ```

3. Run the calculator:

   ```bash
   python calculator.py
   ```

## Features

- Addition, subtraction, multiplication, and division
- Percentage calculation
- Clear button to reset the input
- Equal button to compute the result

## Code

```python
from tkinter import *

def click(event):
    global scvalue
    text = event.widget.cget("text")

    if text == "=":
        try:
            if scvalue.get().isdigit():
                value = int(scvalue.get())
            else:
                value = eval(screen.get())
                scvalue.set(value)
                screen.update()
        except Exception as e:
            scvalue.set("Error")
            screen.update()
    elif text == "C":
        scvalue.set("")
        screen.update()
    else:
        scvalue.set(scvalue.get() + text)
        screen.update()

# Creating the main application window
root = Tk()
root.geometry("400x600")
root.title("Simple Calculator")

# Variable to store the input expression
scvalue = StringVar()
scvalue.set("")

# Entry widget to display the input and result
screen = Entry(root, textvar=scvalue, font="lucida 30 bold", justify=RIGHT)
screen.pack(fill=X, ipadx=8, pady=10, padx=10)

# Creating calculator buttons
buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "0", ".", "=", "+",
    "C"
]

row_val = 1
col_val = 0

for button_text in buttons:
    Button(root, text=button_text, font="lucida 20 bold", padx=20, pady=20).grid(row=row_val, column=col_val, sticky="nsew")
    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1

# Binding click function to all buttons
for i in range(16):
    Button(root, text=buttons[i], font="lucida 20 bold", padx=20, pady=20).grid(row=i // 4 + 1, column=i % 4, sticky="nsew")
    Button(root, text=buttons[i], font="lucida 20 bold", padx=20, pady=20).bind("<Button-1>", click)

# Running the Tkinter event loop
root.mainloop()
```

This simple calculator allows you to perform basic arithmetic operations. 
