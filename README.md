import tkinter as tk


#Function to add text to Entry(TexTbox)
def add_to_expression(value):
    text_box.insert(tk.END,value)

#Function to clear  the Entry(TExbox)
def clear():
    text_box.delete(0,tk.END)

#Function to calculater thr Result
def Calculate():
    try:
        result = eval(text_box.get())
        lab_res.config(text=f"Result: {result}")
    except:
        lab_res.config(text="Error")

#Main root setup
root =tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.config(bg="#222831")
    
# To creating Global variable for styling.
font_txtbox = ("Arial 18")
bg_clr = "#393E46"
fg_cl = "#EEEEEE"
font_label = ("Arial",16,"bold")
font_button = ("Arial",14)
but_clr="#00ADB5"

# Entry Widget (Text Box) fro writting Expression.
text_box= tk.Entry(root,width=16,font=font_txtbox,bd=5,justify="right")
text_box.pack(pady=20)
text_box.config(bg=bg_clr,fg=fg_cl)

#Label Displaying result
lab_res = tk.Label(root, text="Result:", font=font_label,bg=bg_clr,fg=fg_cl)
lab_res.pack()

#Button for Frame
frame_but =tk.Frame(root,bg=bg_clr,)
frame_but.pack()

#Button & position
buttons = [
    ('7',1,0), ('8',1,1), ('9',1,2), ('/',1,3),
    ('4',2,0), ('5',2,1), ('6',2,2), ('*',2,3),
    ('1',3,0), ('2',3,1), ('3',3,2), ('-',3,3),
    ('c',4,0), ('0',4,1), ('=',4,2), ('+',4,3)
]

# Adding the buttons to the Frame
for (text,row,columns)in buttons:
    if text == "=":
        button= tk.Button(frame_but,text=text,font=font_button,width=5,height=2,bg="#00FA9A",fg=fg_cl,command=Calculate)
    elif text =="c": 
        button=tk.Button(frame_but,text=text,font=font_button,width=5,height=2,bg="#00FA9A",fg=fg_cl,command=clear)
    else:
        button=tk.Button(frame_but,text=text,font=font_button,width=5,height=2,bg="#FF5722",fg=fg_cl,command=lambda t=text:add_to_expression(t))
    button.grid(row=row, column=columns, padx=5, pady=5)


root.mainloop()
