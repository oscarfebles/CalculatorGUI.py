# CalculatorGUI.py

import tkinter as tk

root = tk.Tk()
root.title("Calculadora Simple")
root.geometry("300x300")
root.configure(bg = "lightgreen")


#Variable para almacenar la operacion matematica como cadena de texto
calculation = ""

#funcion para agregar un simbolo al calculo
def add_to_calculation(symbol):
    global calculation
    calculation += str(symbol)
    texto_resultado.delete(1.0,"end")
    texto_resultado.insert(1.0, calculation)


#funcion para evaluar calculo y mostrar resultado
def evaluate_calculation():
    global calculation
    try: 
        print(calculation)
        result = str(eval(calculation))
        calculation= ""
        texto_resultado.delete(1.0, "end")
        texto_resultado.insert(1.0, result)
    except: 
        clear_field()
        texto_resultado.insert(1.0, "Error")
        

#funcion para borrar el campo de entrada
def clear_field():
    global calculation
    calculation = ""
    texto_resultado.delete(1.0, "end")
    pass



texto_resultado = tk.Text(root, height=2, width=16, font=("Arial",24))
texto_resultado.grid(columnspan=5)

boton_1 = tk.Button(root, text="1", command=lambda: add_to_calculation (1), width=5, font=("Arial", 14))
boton_1.grid(row=2, column=1)
boton_2 = tk.Button(root, text="2", command=lambda: add_to_calculation (2), width=5, font=("Arial", 14))
boton_2.grid(row=2, column=2)
boton_3 = tk.Button(root, text="3", command=lambda: add_to_calculation (3), width=5, font=("Arial", 14))
boton_3.grid(row=2, column=3)
boton_4 = tk.Button(root, text="4", command=lambda: add_to_calculation (4), width=5, font=("Arial", 14))
boton_4.grid(row=3, column=1)
boton_5 = tk.Button(root, text="5", command=lambda: add_to_calculation (5), width=5, font=("Arial", 14))
boton_5.grid(row=3, column=2)
boton_6 = tk.Button(root, text="6", command=lambda: add_to_calculation (6), width=5, font=("Arial", 14))
boton_6.grid(row=3, column=3)
boton_7 = tk.Button(root, text="7", command=lambda: add_to_calculation (7), width=5, font=("Arial", 14))
boton_7.grid(row=4, column=1)
boton_8 = tk.Button(root, text="8", command=lambda: add_to_calculation (8), width=5, font=("Arial", 14))
boton_8.grid(row=4, column=2)
boton_9 = tk.Button(root, text="9", command=lambda: add_to_calculation (9), width=5, font=("Arial", 14))
boton_9.grid(row=4, column=3)
boton_0 = tk.Button(root, text="0", command=lambda: add_to_calculation (0), width=5, font=("Arial", 14))
boton_0.grid(row=5, column=2)
#SIMBOLOS
boton_SUMA = tk.Button(root, text="+", command=lambda: add_to_calculation ("+"), width=5, font=("Arial", 14))
boton_SUMA.grid(row=2, column=4)
boton_RESTA = tk.Button(root, text="-", command=lambda: add_to_calculation ("-"), width=5, font=("Arial", 14))
boton_RESTA.grid(row=3, column=4)
boton_MULT = tk.Button(root, text="*", command=lambda: add_to_calculation ("*"), width=5, font=("Arial", 14))
boton_MULT.grid(row=4, column=4)
boton_DIV = tk.Button(root, text="/", command=lambda: add_to_calculation ("/"), width=5, font=("Arial", 14))
boton_DIV.grid(row=5, column=4)
boton_IGUAL = tk.Button(root, text="=", command=evaluate_calculation, width=5, font=("Arial", 14))
boton_IGUAL.grid(row=5, column=3)
boton_COMA = tk.Button(root, text=".", command=lambda: add_to_calculation ("."), width=5, font=("Arial", 14))
boton_COMA.grid(row=5, column=1)


root.mainloop()


