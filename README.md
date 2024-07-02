# مشروع بايثون لحساب زكاة المال
from tkinter import *
from tkinter import messagebox
# إنشاء واجهة المستخدم
window = Tk()
window.geometry("600x350")
window.resizable(0, 0)
window.config(bg="lightblue")
window.title("حاسبة زكاة المال")
# نصاب الزكاة بالدولار
nisab = 442
# إنشاء متغير لتخزين قيمة أموالك
money = DoubleVar()

# دالة حساب الزكاة
def calculate_zakat():
    try:
        money = float(money_entry.get())
        zakat_amount = money * 0.025 if money > nisab else 0
        result_label.config(
            text=f"قيمة الزكاة الواجبة عليك هي: {zakat_amount:.2f} دولار"
        )
    except ValueError:
        messagebox.showerror("خطأ", "الرجاء إدخال قيمة صالحة.")

Label(
    window,
    text="أدخل قيمة أموالك بالدولار",
    font="Tahoma 14",
    fg="gray",
    justify="right",
).place(x=200, y=20)
money_entry = Entry(window, textvariable=money, font="tahomab 12")
money_entry.place(x=200, y=70)

# إنشاء زر الحساب
calculate_button = Button(
    window,
    text="حساب الزكاة",
    font="tahoma 14 bold",
    bg="lightgreen",
    padx=2,
    command=calculate_zakat,
    justify="right",
)
calculate_button.place(x=220, y=120)

# إنشاء تسمية لعرض النتيجة
result_label = Label(
    window, text="", font="tahoma 14 bold", bg="lightblue", justify="right"
)
result_label.place(x=100, y=180)

window.mainloop()
