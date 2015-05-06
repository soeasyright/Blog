title: "Tkinter "
date: 2015-04-18 22:59:04
tags: [python,python GUI,tkinter]
categories: [python,senior]
---

```
try:
    # for Python2
    from Tkinter import *
except ImportError:
    # for Python3
    from tkinter import *
```
使用 Tk 首先要 import tkinter ，這裡用 from ， import 之後星號表示所有名稱，這使我們在程式中可以直接使用 tkinter 中的名稱，不需要連帶寫出 tkinter
```
root = Tk() ##create TK object
some = Label(root, text="Hello World!", width="30", height="5") ## Label with "Hello World"
some.pack()
root.mainloop()
```

```
class GUIDemo(Frame):
    def __init__(self, master=None):
        Frame.__init__(self, master)
        self.grid()
        self.createWidgets()

    def createWidgets(self):
        self.inputText = Label(self)
        self.inputText["text"] = "Name:"
        self.inputText.grid(row=0, column=0)

        self.inputField = Entry(self)
        self.inputField["width"] = 50
        self.inputField.grid(row=0, column=1, columnspan=3)

        self.submit = Button(self)
        self.submit["text"] = "submit"
        self.submit.grid(row=2, column=3)
        self.submit["command"] =  self.submitMethod

        self.displayText = Label(self)
        self.displayText["text"] = ""
        self.displayText.grid(row=3, column=0, columnspan=3)
    def submitMethod(self):
        self.displayText["text"] = "Hello %s" % self.inputField.get()


if __name__ == '__main__':
    root = Tk()
    app = GUIDemo(master=root)
    app.mainloop()
```