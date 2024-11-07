# calci.py
from tkinter import *

calculator = Tk()
calculator.geometry("312x324")
calculator.resizable(0,0)
calculator.title("Calculator")

expression = ""
input_text = StringVar()

input_frame = Frame(calculator, width = 312, height = 50, bd = 0, highlightbackground = "green", highlightcolor = "green", highlightthickness = 1)
input_frame.pack(side = TOP)
input_field = Entry(input_frame, font = ("arial", 18, "bold"), textvariable = input_text, width = 50, background = "#eee", bd = 0, justify = RIGHT)
input_field.grid(row = 0, column = 0)
input_field.pack(pady = 10)

def btn_click(item):
    global expression
    expression += str(item)
    input_text.set(expression)

def btn_all_clear():
    global expression
    expression = ""
    input_text.set(expression)

def btn_clear():
    global expression
    if expression: 
        expression = expression[:-1]  # Remove last character
        input_text.set(expression)

def btn_equal():
    global expression
    try:
        result = str(eval(expression))
        input_text.set(result)
        expression = result  # Update the expression to the result
    except:
        input_text.set("Error")
        expression = ""

def key_press(event):
    # Map keyboard inputs to calculator buttons
    key = event.char
    if key in '0123456789+-*/.':
        btn_click(key)
    elif key == '\r':  # Enter key
        btn_equal()
    elif key == '\x08':  # Backspace key
        btn_clear()

calculator.bind("<Key>", key_press)

buttons = Frame(calculator, width = 312, height = 270, bd = 0, bg = "black")
all_clear = Button(buttons, text = "AC", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = btn_all_clear).grid(row = 0, column = 0, padx = 1, pady = 1)
clear = Button(buttons, text = "C", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = btn_clear).grid(row = 0, column = 1, padx = 1, pady = 1)
module = Button(buttons, text = "%", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = lambda: btn_click('%')).grid(row = 0, column = 2, padx = 1, pady = 1)
divide = Button(buttons, text = "/", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = lambda: btn_click('/')).grid(row = 0, column = 3, padx = 1, pady = 1)

seven = Button(buttons, text = "7", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('7')).grid(row = 1, column = 0, padx = 1, pady = 1)
eight = Button(buttons, text = "8", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('8')).grid(row = 1, column = 1, padx = 1, pady = 1)
nine = Button(buttons, text = "9", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('9')).grid(row = 1, column = 2, padx = 1, pady = 1)
multiple = Button(buttons, text = "*", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = lambda: btn_click('*')).grid(row = 1, column = 3, padx = 1, pady = 1)

four = Button(buttons, text = "4", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('4')).grid(row = 2, column = 0, padx = 1, pady = 1)
five = Button(buttons, text = "5", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('5')).grid(row = 2, column = 1, padx = 1, pady = 1)
six = Button(buttons, text = "6", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('6')).grid(row = 2, column = 2, padx = 1, pady = 1)
minus = Button(buttons, text = "-", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = lambda: btn_click('-')).grid(row = 2, column = 3, padx = 1, pady = 1)

one = Button(buttons, text = "1", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('1')).grid(row = 3, column = 0, padx = 1, pady = 1)
two = Button(buttons, text = "2", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('2')).grid(row = 3, column = 1, padx = 1, pady = 1)
three = Button(buttons, text = "3", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('3')).grid(row = 3, column = 2, padx = 1, pady = 1)
plus = Button(buttons, text = "+", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = lambda: btn_click('+')).grid(row = 3, column = 3, padx = 1, pady = 1)

# two_zero = Button(buttons, text = "00", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2").grid(row = 4, column = 0, padx = 1, pady = 1)
zero = Button(buttons, text = "0", fg = "black", width = 21, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('0')).grid(row = 4, column = 0, columnspan = 2, padx = 1, pady = 1)
point = Button(buttons, text = ".", fg = "black", width = 10, height = 3, bd = 0, bg = "#fff", cursor = "hand2", command = lambda: btn_click('.')).grid(row = 4, column = 2, padx = 1, pady = 1)
equal = Button(buttons, text = "=", fg = "black", width = 10, height = 3, bd = 0, bg = "#a9a9a9", cursor = "hand2", command = btn_equal).grid(row = 4, column = 3, padx = 1, pady = 1)

buttons.pack()
calculator.mainloop()
