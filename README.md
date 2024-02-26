import PySimpleGUI as sg

# Define a function to convert a word to pig Latin
def pig_latin(word):
    # If the word is empty, return an empty string
    if not word:
        return ""
    # If the word starts with a vowel, add "way" at the end
    elif word[0] in "aeiou":
        return word + "way"
    # Otherwise, move the first letter to the end and add "ay"
    else:
        return word[1:] + word[0] + "ay"

# Define the window title and layout
title = "PigLatinGUI"
layout = [
    [sg.Text("Enter a word:")],
    [sg.Input(key="-WORD-")],
    [sg.Text("Pig Latin version:"), sg.Text(size=(15,1), key="-OUTPUT-")],
    [sg.Button("Convert"), sg.Button("Exit")]
]

# Create the window object
window = sg.Window(title, layout)

# Create the event loop
while True:
    # Read the event and values from the window
    event, values = window.read()
    # If the user clicks the exit button or the X button, break the loop
    if event == "Exit" or event == sg.WIN_CLOSED:
        break
    # If the user clicks the convert button, get the word from the input widget
    elif event == "Convert":
        word = values["-WORD-"]
        # Convert the word to pig Latin
        pig_word = pig_latin(word)
        # Update the output widget with the pig Latin word
        window["-OUTPUT-"].update(pig_word)

# Close the window
window.close()
