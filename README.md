# michael-jordan-game
hes a subatomic particle
import tkinter as tk
import random

class FindMJGame:
    def __init__(self, root):
        self.root = root
        self.root.title("Find Michael Jordan!")
        self.score = 0

        self.label = tk.Label(root, text="Click to find Michael Jordan!", font=("Helvetica", 16))
        self.label.pack(pady=20)

        self.canvas = tk.Canvas(root, width=400, height=400, bg="lightblue")
        self.canvas.pack()

        self.canvas.bind("<Button-1>", self.check_click)
        self.place_mj()

    def place_mj(self):
        # Randomly place MJ (as a tiny dot) on the canvas
        self.mj_x = random.randint(0, 390)
        self.mj_y = random.randint(0, 390)
        self.canvas.create_oval(self.mj_x, self.mj_y, self.mj_x + 1, self.mj_y + 1, fill="black", tags="mj")

    def check_click(self, event):
        if abs(event.x - self.mj_x) <= 1 and abs(event.y - self.mj_y) <= 1:
            self.score += 1
            self.label.config(text=f"Found him! Score: {self.score}")
            self.canvas.delete("mj")
            self.place_mj()
        else:
            self.label.config(text=f"Missed! Score: {self.score}")

if __name__ == "__main__":
    root = tk.Tk()
    game = FindMJGame(root)
    root.mainloop()
