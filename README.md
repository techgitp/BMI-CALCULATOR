# BMI-CALCULATOR
import tkinter as tk
from tkinter import messagebox

def calculate_bmi():
    try:
        weight = float(weight_entry.get())
        height = float(height_entry.get())
        
        if weight <= 0 or height <= 0:
            messagebox.showerror("Input Error", "Weight and height must be positive numbers.")
            return
        
        bmi = weight / (height ** 2)
        category = classify_bmi(bmi)
        
        result_label.config(text=f"Your BMI is: {bmi:.2f}\nCategory: {category}")
    
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numeric values.")

def classify_bmi(bmi):
    """Classify BMI into categories"""
    if bmi < 18.5:
        return "Underweight"
    elif 18.5 <= bmi < 24.9:
        return "Normal weight"
    elif 25 <= bmi < 29.9:
        return "Overweight"
    else:
        return "Obesity"

# Create the main window
root = tk.Tk()
root.title("BMI Calculator")

# Create and place the labels and entry fields
tk.Label(root, text="Weight (kg):").grid(row=0, column=0)
weight_entry = tk.Entry(root)
weight_entry.grid(row=0, column=1)

tk.Label(root, text="Height (m):").grid(row=1, column=0)
height_entry = tk.Entry(root)
height_entry.grid(row=1, column=1)

# Create and place the calculate button
calculate_button = tk.Button(root, text="Calculate BMI", command=calculate_bmi)
calculate_button.grid(row=2, columnspan=2)

# Create and place the result label
result_label = tk.Label(root, text="")
result_label.grid(row=3, columnspan=2)

# Start the GUI event loop
root.mainloop()
