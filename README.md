# GUI-tkinter-wallpaper-changer
# import modules
from wallpaper import set_wallpaper, get_wallpaper
# import modules
from tkinter import *
from tkinter import filedialog
from wallpaper import set_wallpaper
# get current wallpaper's path
print(get_wallpaper())
 
# set your photo
set_wallpaper("location/to/image.jpg")
 
# user define function
def change_wall():
   
    # seting your photo
    try:
        set_wallpaper(str(path.get()))
        check = "voila!"
 
    except:
 
        check = "Beep.Beep.Error!"
    result.set(check)
 
 
def browseFiles():
    filename = filedialog.askopenfilename(initialdir="/",
                                          title="Select a File",
                                          filetypes=(("jpeg files", "*.jpg"), ("all files", "*.*")))
    path.set(filename)
     
    # Changing label contents
    label_file_explorer.configure(text="File Opened: "+filename)
    return filename
 
 
# object of tkinter GUI
# and background set for red
master = Tk()
master.configure(bg='light grey')
 
# Variable Classes in tkinter GUI
result = StringVar()
path = StringVar()
 
 
label_file_explorer = Label(
    master, text="Select a image", width=100, fg="blue")
 
 
# Creating label content for each information
# naming using widget Label
Label(master, text="Select image : ", bg="light grey").grid(row=0, sticky=W)
Label(master, text="Status :", bg="light grey").grid(row=3, sticky=W)
 
 
# Creating label for class variable
# naming by the use of widget Entry
Label(master, text="", textvariable=result,
      bg="light grey").grid(row=3, column=1, sticky=W)
 
# creating a button using the widget
# Button will call the submit function
b = Button(master, text="Open", command=browseFiles, bg="white")
b.grid(row=0, column=2, columnspan=2, rowspan=2, padx=5, pady=5,)
 
label_file_explorer.grid(column=1, row=1)
 
c = Button(master, text="Apply", command=change_wall, bg="white")
c.grid(row=2, column=2, columnspan=2, rowspan=2, padx=5, pady=5,)
 
mainloop()
