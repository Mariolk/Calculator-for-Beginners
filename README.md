
**HOW TO USE IT**

def press(num): # Function to show the number on the screen
    global expression
    expression = expression + str(num)
    screen_text.set(expression)

def equalpress(): # Function to solve the mathematical expression
    global expression
    try:
        global expression
        result = str(eval(expression)) # Evaluate the expression to number
        screen_text.set(result) # Show the result on the screen
    except Exception as e:
        messagebox.showerror('Error', 'Not valid entry') # Show error message
        screen_text.set('') #  Clear screen
        expression = '' # Clear the expression
    
def clear(): # Function to clear the screen
    global expression
    expression = ''
    screen_text.set('')

# BUTTONS NUMBERS AND OPERATORS 

buttons = [
    ('7',1, 0), ('8',1, 1), ('9',1, 2), ('/', 1, 3),
    ('4',2, 0), ('5',2, 1), ('6',2, 2), ('*', 2, 3),
    ('1',3, 0), ('2',3, 1), ('3',3, 2), ('-', 3, 3),
    ('0',4, 0), ('.',4, 1), ('+',4, 2)

]

for (text, row, col) in buttons: # Create the buttons
    button = tk.Button(root, text=text, width=5, height=2, font=('Arial', 18), bg=color_boton, fg=color_texto, command=lambda t=text: press(t))
    button.grid(row=row, column=col, padx=5, pady=5, sticky='nsew') # Positioning

# EQUAL BUTTON

equal_button = tk.Button(root, text='=', width=5, height=2, font=('Arial', 18), bg=color_boton_igual, fg=color_texto, command=equalpress)
equal_button.grid(row=4, column=3, padx=5, pady=5, sticky='nsew') # Positioning

#BOTON CLEAR

clear_button = tk.Button(root, text='C', width=5, height=2, font=('Arial', 18), bg=color_boton_clear, fg=color_texto, command=clear)
clear_button.grid(row=5, column=0, columnspan=4, padx=5, pady=5, sticky='nsew') # Positioning

# Configure the grid
for i in range(5): 
    root.grid_rowconfigure(i, weight=1)
for i in range(4):
    root.grid_columnconfigure(i, weight=1)

root.mainloop() # Show the window
