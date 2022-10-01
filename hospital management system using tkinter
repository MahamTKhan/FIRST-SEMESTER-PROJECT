#======================First Python database project using tkinter and ms access=================
import tkinter
from tkinter import *
from tkinter import ttk
from tkinter import messagebox
from PIL import ImageTk,Image
from tkcalendar import DateEntry
import pyodbc

#===============================title window=======================================
main=Tk()
main.title("SM HOSPITAL APPLICATION")
main.geometry("1300x715")
main.configure(background="#dbd8d7")
bg=PhotoImage(file=r'C:\Users\HP\Desktop\33.png')
l1=Label(main,image=bg)
l1.place(x=0,y=0)
l2=Label(main,text="WELCOME!",font=("Times New Roman",15),bd=10,width=15,height=5,bg="LIGHT BLUE",fg="BLACK")
l2.pack(side=TOP,fill=X)


#===============================================exit function for page 1===========================================

def exit1():
    main.destroy()

b1=Button(main,text="EXIT",bg="grey",width=20,height=5,command=exit1)
b1.pack(anchor='s',side=LEFT)

#================================================next function for page 1===============================================

def next1():
    #next function for page 1
    #connecting page 2 (dashboard)
    dashboard=Toplevel()
    dashboard.geometry("1700x1500")
    l1 = Label(dashboard,text="WELCOME TO THE SM HOSPITAL DASHBOARD", width=25, bg="red", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
    l1.pack(side=TOP, fill=X)
    l2 = Label(dashboard,text="YOUR HEALTH IS OUR FIRST PRIORITY", width=15, bg="green", fg="white", font=100, bd=25, pady=50,padx=20)
    l2.pack(side=BOTTOM, fill=X)
    f1 = Frame(dashboard, bg="white", bd=20)
    f1.place(x=0, y=100, width=1400, height=500)


    #====================================================exit function for exit button of page2=====================================================

    def exit2():
        dashboard.destroy()

    b2 = Button(f1, text="EXIT", bg="GREY", fg="white", font=("bold", 15), width=25, height=5, bd=10,command=exit2).place(relx=0.09, rely=0.5, anchor=W)

    #==============================================signin function for sign in button of page2=========================================

    def signin():
        def cmd():
            first_name = e1.get()
            last_name = e2.get()

            password = e4.get()
            if first_name == "" or last_name == "" or password == "":
                messagebox.showerror("error","All fields are required ")
            else:
                con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                                     r'DBQ=C:\Users\HP\Desktop\Database51.accdb')
                cur1 = con.cursor()
                userdata = cur1.execute(
                    "Select * from Signup where First_name='" + first_name + "' and Last_Name='" + last_name + "'and Password='" + password + "'")
                data = userdata.fetchall()
                print(data)
                if (len(data) > 0):
                    messagebox.showinfo("Success", "Successfully Login")
                    next2()
                else:
                    messagebox.showerror("Error", "Invalid Information")

                con.commit()
                con.close()

        root = Toplevel()
        root.geometry("1500x1500")
        l = Label(root, text="PATIENT PORTAL", width=25, bg="BLUE", fg="white", bd=20, font=("Times New Roman", 25),
                  pady=10, padx=10)
        l.pack(side=TOP, fill=X)

        l1 = Label(root, text='''FIRST NAME''', width=10)
        l1.place(relx=0.4, rely=0.3, anchor='s')
        e1 = Entry(root)
        e1.place(relx=0.5, rely=0.3, anchor='s', width=190)

        l2 = Label(root, text='''LAST NAME''')
        l2.place(relx=0.4, rely=0.4, anchor='s')
        e2 = Entry(root)
        e2.place(relx=0.5, rely=0.4, anchor='s', width=190)


        l4 = Label(root, text='''PASSWORD''')
        l4.place(relx=0.4, rely=0.5, anchor='s')
        e4 = Entry(root, show="*")
        e4.place(relx=0.5, rely=0.5, anchor='s', width=190)


        #================================================back  button function for patient portal(page3)===============================================
        def back():
            dashboard = Toplevel()

            dashboard.geometry("1700x1500")
            l1 = Label(dashboard, text="WELCOME TO THE SM HOSPITAL DASHBOARD", width=25, bg="red", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
            l1.pack(side=TOP, fill=X)
            l2 = Label(dashboard, text="YOUR HEALTH IS OUR FIRST PRIORITY", width=15, bg="green", fg="white", font=100,bd=25, pady=50, padx=20)
            l2.pack(side=BOTTOM, fill=X)
            f1 = Frame(dashboard, bg="white", bd=20)
            f1.place(x=0, y=100, width=1400, height=500)

            # ==============================================exit function for exit button of page2=======================================

            b2 = Button(f1, text="EXIT", bg="GREY", fg="white", font=("bold", 15), width=25, height=5, bd=10,command=exit2).place(relx=0.09, rely=0.5, anchor=W)

            # =====================================================signin function for page2================================================

            b2 = Button(f1, text="SIGN IN", bg="GREY", fg="white", font=("bold", 15), width=25, height=5, bd=10,command=signin).place(relx=0.38, rely=0.5, anchor=W)

            # ===================================================signup function for page 2======================================================

            b1 = Button(f1, text="SIGN UP", bg="GREY", fg="white", font=("bold", 15), width=25, height=5,bd=10,command=signup).place(relx=0.78, rely=0.5, anchor=CENTER)



        # =======================================================next function for patient portal=======================================
        def next2():
            window=Toplevel()
            window.geometry("1500x1500")
            l1 = Label(window, text="ENABLING EASY ACCESS", width=25, bg="BLUE", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
            l1.pack(side=TOP, fill=X)
            l2 = Label(window, text="YOUR HEALTH IS OUR FIRST PRIORITY", width=5, bg="green", fg="white",font=("Times New Roman", 15), bd=25, pady=50, padx=20)
            l2.pack(side=BOTTOM, fill=X)

            def docrecord():
                root2 = Toplevel()
                root2.geometry("1500x1500")
                l1 = Label(root2, text="WE HAVE THE BEST DOCTORS OF PAKISTAN", width=25, bg="red", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
                l1.pack(side=TOP, fill=X)

                my_tree = ttk.Treeview(root2)
                my_tree['columns'] = ("Name", "ID", "specialization")

                my_tree.column("#0", anchor=W, width=120)
                my_tree.column("Name", anchor=W, width=120)
                my_tree.column("ID", anchor=CENTER, width=80)
                my_tree.column("specialization", anchor=W, width=120)

                my_tree.heading("#0", text="DESIGNATION", anchor=W)
                my_tree.heading("Name", text="Name", anchor=W)
                my_tree.heading("ID", text="ID", anchor=CENTER)
                my_tree.heading("specialization", text="specialization", anchor=W)

                my_tree.insert(parent='', index='end', iid=0, text="SURGEON",values=("DR AHMED", 1, "HEART SPECIALIST"))
                my_tree.insert(parent='', index='end', iid=1, text="SURGEON", values=("DR MAHAM", 2, "NEUROLOGIST"))
                my_tree.insert(parent='', index='end', iid=2, text="SURGEON", values=("DR USMAN", 3, "EYE SPECIALIST"))
                my_tree.insert(parent='', index='end', iid=3, text="GENERAL", values=("DR HANIA", 4, "PSYCHIATRIST"))
                my_tree.insert(parent='', index='end', iid=4, text="SURGEON", values=("DR SARA", 5, "PULMUNOLOGIST"))
                my_tree.insert(parent='', index='end', iid=5, text="GENERAL", values=("DR MAHEEN", 6, "PEDIATRICIAN"))

                my_tree.pack(pady=150)

                def back2():
                    window = Toplevel()
                    window.geometry("1500x1500")
                    l1 = Label(window, text="ENABLING EASY ACCESS", width=25, bg="BLUE", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
                    l1.pack(side=TOP, fill=X)
                    l2 = Label(window, text="YOUR HEALTH IS OUR FIRST PRIORITY", width=5, bg="green", fg="white",font=("Times New Roman", 15), bd=25, pady=50, padx=20)
                    l2.pack(side=BOTTOM, fill=X)

                    b1 = Button(window, text="APPOINTMENT", bg="light GREY", fg="black", font=("bold", 15), width=25,height=5, bd=10).place(relx=0.18, rely=0.4, anchor=W)
                    b2 = Button(window, text="DOCTOR RECORD", bg="light GREY", fg="black", font=("bold", 15), width=25,height=5, bd=10, command=docrecord).place(relx=0.58, rely=0.4, anchor=W)

                b1 = Button(root2, text="BACK", bg="grey", width=20, height=5, command=back2)
                b1.place(relx=0.1, rely=0.9, anchor='s')

            def appointment():
                root1=Toplevel()

                def done():
                    fir_name = e1.get()
                    las_name = e2.get()
                    doctor_name = clicked.get()
                    date = cal.get()
                    contactno = e3.get()
                    particulars = e4.get()
                    if fir_name == "":
                        messagebox.showerror('Error','Please enter your first name')
                    elif las_name == "":
                        messagebox.showerror('Error','Please enter your last name')
                    elif doctor_name == "":
                        messagebox.showerror('Error','Please select the doctor')
                    elif contactno == "":
                        messagebox.showerror('Error','Please enter your contact number')
                    else:
                        con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                                             r'DBQ=C:\Users\HP\Desktop\Database51.accdb')
                        cur = con.cursor()
                        cur.execute(
                            f"INSERT INTO Appointment(First_Name,Last_Name,Doctor,Contact_No,Select_Date,Any_paticulars) values('{fir_name}','{las_name}','{doctor_name}','{contactno}','{date}','{particulars}')")
                        con.commit()
                        con.close()
                        messagebox.showinfo('Success', "your appointment has been booked")


                root1.geometry("1600x1500")

                l = Label(root1,text="BOOK YOUR APPOINTMENT", width=25, bg="BLUE", fg="white", bd=20,font=("Times New Roman", 25), pady=10, padx=10)
                l.pack(side=TOP, fill=X)

                l1 = Label(root1, text='''FIRST NAME''', width=10)
                l1.place(relx=0.4, rely=0.3, anchor='s')
                e1 = Entry(root1)
                e1.place(relx=0.5, rely=0.3, anchor='s', width=190)


                l2 = Label(root1,text='''LAST NAME''')
                l2.place(relx=0.4, rely=0.4, anchor='s')
                e2 = Entry(root1)
                e2.place(relx=0.5, rely=0.4, anchor='s', width=190)


                l3 = Label(root1,text=''' DOCTOR''')
                l3.place(relx=0.4, rely=0.5, anchor='s')

                l4 = Label(root1,text='''SELECT DATE''')
                l4.place(relx=0.39, rely=0.6, anchor='s')

                l5 = Label(root1,text='''CONTACT NO.''')
                l5.place(relx=0.38, rely=0.7, anchor='s')
                e3 = Entry(root1)
                e3.place(relx=0.5, rely=0.7, anchor='s', width=200)

                l6 = Label(root1,text='''ANY PARTICULARS''')
                l6.place(relx=0.38, rely=0.8, anchor='s')
                e4 = Entry(root1)
                e4.place(relx=0.5, rely=0.8, anchor='s', width=200)

                def show():
                    label.config(text=clicked.get())

                options = [
                    "DR AHMED",
                    "DR MAHAM",
                    "DR USMAN",
                    "DR HANIA",
                    "DR SARA",
                    "DR MAHEEN"
                ]

                clicked = StringVar()

                clicked.set("DR AHMED")
                drop = OptionMenu(root1, clicked, *options)
                drop.place(relx=0.45, rely=0.46)
                button = Button(root1, text="CONFIRM", command=show).place(relx=0.55, rely=0.46)

                cal = DateEntry(root1, width=12, year=2019, month=6, day=22,background='darkblue', foreground='white', borderwidth=2)
                cal.place(relx=0.45, rely=0.575)
                label = Label(root1, text=" ")
                label.place(relx=0.6, rely=0.46)
                b1 = Button(root1, text="DONE", bg="grey", width=20, height=5, command=done)
                b1.place(relx=0.1, rely=0.9, anchor='s')

                def next3():
                    end=Toplevel()
                    end.geometry("1700x1500")
                    end.title("SM HOSPITAL APPLICATION")
                    l1 = Label(end, text="SM HOSPITAL", width=15, bg="BLUE", fg="white", font=("Times New Roman", 25),
                               bd=25, pady=50, padx=20)
                    l1.pack(side=TOP, fill=X)
                    l2 = Label(end, text="THANKYOU FOR REGISTERING YOUR APPOINTMENT", width=75, height=10, bg="red",
                               fg="white", bd=20, font=("Times New Roman", 25), pady=10, padx=10)
                    l2.place(relx=0.0, rely=0.2)
                    l3 = Label(end, text="YOUR HEALTH IS OUR FIRST PRIORITY", width=15, bg="green", fg="white",
                               font=("Times New Roman", 25), bd=25, pady=50, padx=20)
                    l3.pack(side=BOTTOM, fill=X)

                b2 = Button(root1, text="NEXT", bg="grey", width=20, height=5,command=next3)
                b2.place(relx=0.9, rely=0.9, anchor='s')


            b1 = Button(window,text="APPOINTMENT", bg="light GREY", fg="black", font=("bold", 15), width=25,height=5, bd=10,command=appointment).place(relx=0.18, rely=0.4,anchor=W)
            b2 = Button(window,text="DOCTOR RECORD", bg="light GREY", fg="black", font=("bold", 15), width=25,height=5, bd=10, command=docrecord).place(relx=0.58, rely=0.4, anchor=W)

        b1 = Button(root, text="BACK", bg="grey", width=20, height=5, command=back)
        b1.place(relx=0.1, rely=0.9, anchor='s')
        b2 = Button(root, text="NEXT", bg="grey", width=20, height=5, command=cmd)
        b2.place(relx=0.9, rely=0.9, anchor='s')


    #=============================================================calling sign in button for page 2===================================================
    b2 = Button(f1, text="SIGN IN", bg="GREY", fg="white", font=("bold", 15), width=25, height=5, bd=10,command=signin).place(relx=0.38, rely=0.5, anchor=W)

    # ========================================================sign up function for sign up button of page2*===============================================
    def signup():
        m=Toplevel()
        m.geometry("1350x700+0+0")

        def action():
            fname = e1.get()
            lname = e2.get()
            age = e3.get()
            cont = e4.get()
            passw = e5.get()
            cpass = e6.get()
            if fname == "" or lname == "" or age == "" or cont == "" or passw == "":
                messagebox.showerror('Error', 'All fields are required')
            elif passw != cpass:
                messagebox.showerror('Error', 'Password Mismatch')

            else:
                con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                                     r'DBQ=C:\Users\HP\Desktop\Database51.accdb')
                cur = con.cursor()
                cur.execute(
                    f"INSERT INTO Signup(First_name,Last_name,Age,Contact,Password,Conf_pass) values('{fname}','{lname}','{age}','{cont}','{passw}',{cpass})")
                con.commit()
                con.close()
                messagebox.showinfo("Success","Your account has been created")

        l1 = Label(m,text="CREATE  AN  ACCOUNT", width=25, bg="blue", fg="white", bd=20, font=("Times New Roman", 25))
        l1.pack(side=TOP, fill=X)
        label1 = Label(m, text="First Name", font=17).place(relx=0.4, rely=0.2)
        label2 = Label(m, text="Last Name", font=17).place(relx=0.4, rely=0.3)
        label3 = Label(m, text="Age", font=17).place(relx=0.4, rely=0.4)
        label4 = Label(m, text="Contact No", font=17).place(relx=0.4, rely=0.5)
        label5 = Label(m, text="Password", font=17).place(relx=0.4, rely=0.6)
        label6 = Label(m, text="Confirm Password", font=17).place(relx=0.4, rely=0.7)
        e1 = Entry(m, width=27)
        e1.place(relx=0.5, rely=0.2)
        e2 = Entry(m, width=27)
        e2.place(relx=0.5, rely=0.3)
        e3 = Entry(m, width=27)
        e3.place(relx=0.5, rely=0.4)
        e4 = Entry(m, width=27)
        e4.place(relx=0.5, rely=0.5)
        e5 = Entry(m, show="*", width=27)
        e5.place(relx=0.5, rely=0.6)
        e6 = Entry(m, show="*", width=27)
        e6.place(relx=0.5, rely=0.7)
        button = Button(m, text="Submit", width=10, command=action).place(relx=0.5, rely=0.8)

    #==================================================calling signup function for page 2================================================
    b1 = Button(f1, text="SIGN UP", bg="GREY", fg="white", font=("bold", 15), width=25, height=5, bd=10,command=signup).place(relx=0.78, rely=0.5, anchor=CENTER)


#========================================================next function button for page1====================================================

b2=Button(main,text="NEXT",bg="grey",width=20,height=5,command=next1)
b2.pack(anchor='s',side=RIGHT)


main.mainloop()
