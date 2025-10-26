from tkinter import messagebox

# Function to check the winner
def check_winner():
    for row in range(3):
        if buttons[row][0]["text"] == buttons[row][1]["text"] == buttons[row][2]["text"] != "":
            return buttons[row][0]["text"]

    for col in range(3):
        if buttons[0][col]["text"] == buttons[1][col]["text"] == buttons[2][col]["text"] != "":
            return buttons[0][col]["text"]

    if buttons[0][0]["text"] == buttons[1][1]["text"] == buttons[2][2]["text"] != "":
        return buttons[0][0]["text"]

    if buttons[0][2]["text"] == buttons[1][1]["text"] == buttons[2][0]["text"] != "":
        return buttons[0][2]["text"]

    return None

# Function to handle button click
def button_click(row, col):
    if buttons[row][col]["text"] == "" and game_over == False:
        buttons[row][col]["text"] = current_player[0]
        winner = check_winner()

        if winner:
            messagebox.showinfo("Game Over", f"Player {winner} wins!")
            reset_game()
        elif all(button["text"] != "" for row in buttons for button in row):
            messagebox.showinfo("Game Over", "It's a draw!")
            reset_game()
        else:
            switch_player()

# Function to switch between players
def switch_player():
    global current_player
    current_player = "O" if current_player == "X" else "X"

# Function to reset the game
def reset_game():
    global game_over, current_player
    game_over = False
    current_player = "X"
    for row in range(3):
        for col in range(3):
            buttons[row][col]["text"] = ""

# Create the main window
root = tk.Tk()
root.title("Tic-Tac-Toe")

# Initialize variables
buttons = [[None, None, None] for _ in range(3)]
game_over = False
current_player = "X"

# Create buttons for the Tic-Tac-Toe grid
for row in range(3):
    for col in range(3):
        buttons[row][col] = tk.Button(root, text="", width=10, height=3, font=("Arial", 24),
                                      command=lambda r=row, c=col: button_click(r, c))
        buttons[row][col].grid(row=row, column=col)

# Run the Tkinter event loop
root.mainloop()
