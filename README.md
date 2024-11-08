## Steps to Run the Program

1. **Open the Online Compiler:**
   - Go to [online-python.com](https://online-python.com).

2. **Clear the `main.py` File:**
   - Delete the code inside the `main.py` file.

3. **Replace Code in `main.py`:**
   - Copy and paste the following code into the `main.py` file on online-python.com:

   ```python
   def analyze_file(file_path):
       try:
           # Assume UTF-8 encoding and open the file in read mode
           with open(file_path, 'r') as file:
               content = file.read()
           
           # Extract the file name from the file path
           file_name = file_path.split('/')[-1]
           
           # Handle the case where the file is empty or contains only whitespace
           if not content or content.isspace():
               return {
                   "File Name": file_name,
                   "Total Characters (excluding whitespace)": 0,
                   "Letters": 0,
                   "Digits": 0,
                   "Other Characters": 0,
                   "Number of Words": 0
               }
           
           # Count the number of letters, digits, and other characters
           letters = sum(c.isalpha() for c in content)
           digits = sum(c.isdigit() for c in content)
           other_chars = sum(not c.isalnum() and not c.isspace() for c in content)
           
           # Calculate the total number of characters, excluding whitespace
           total_chars = letters + digits + other_chars
           
           # Analyze the words in the file content
           words = content.split()
           num_words = len(words)
           word_lengths = {}
           
           # Count the number of words of each length
           for word in words:
               # Only count the length of words that contain letters
               letter_count = len(''.join(c for c in word if c.isalpha()))
               if letter_count > 0:
                   word_lengths[letter_count] = word_lengths.get(letter_count, 0) + 1
           
           # Compile the analysis report
           report = {
               "File Name": file_name,
               "Total Characters": total_chars,
               "Letters": letters,
               "Digits": digits,
               "Other Characters": other_chars,
               "Number of Words": num_words
           }
           
           # Add the word length distribution to the report
           for length, count in sorted(word_lengths.items()):
               report[f"{length}-letter Words"] = count
           
           return report
       
       # Handle various exceptions that may occur during file processing
       except FileNotFoundError:
           print(f"The file '{file_path}' was not found.")
           return None
       except UnicodeDecodeError:
           print(f"The file '{file_path}' could not be decoded. UTF-8 expected")
           return None
       except PermissionError:
           print(f"Access denied - Permissions Error '{file_path}'.")
           return None

   def main():
       file_path = 'parameters.txt'
       file_report = analyze_file(file_path)
       
       # Print the analysis report if it was successfully generated
       if file_report:
           print("\nFile Analysis Report:")
           print("-" * 20)
           for key, value in file_report.items():
               print(f"{key}: {value}")

   # Execute the main function when the script is run directly
   if __name__ == "__main__":
       main()
    ```

4. **Add a New File:**
   - Click the "+" icon next to `main.py` in the navbar.
   - Name the new file **`parameters.txt`**.
   - Copy the content below or from the `parameters.txt` file in the zip folder and paste it into the `parameters.txt` file in the IDE.

        ```txt
This is a sample text file for testing purposes.
It contains multiple lines, characters, words, and different types of content.

Numbers are also included: 12345, 67890, 13579, and some special characters !@#$%^&*().

Here's a line with punctuation... does it work?

The quick brown fox jumps over the lazy dog.

The file should include:
- Short words like I, am, he, on.
- Longer words such as 'parameter', 'assessment', and 'characterization'.

And a few VERY long words:
- pneumonoultramicroscopicsilicovolcanoconiosis (45 letters)
	Coined in 1935 by then-president of the National Puzzlers' League, Everett M. Smith.
- antidisestablishmentarianism (28 letters)

Thank you for giving me this opportunity.
    ```

5. **Run the Program:**
   - Go back to `main.py`.
   - On the bottom left corner of the IDE, press the **Run** button.
   - View the program output in the command line area at the bottom of the screen.
  

## Common Errors

- **SyntaxError: invalid syntax**
   - **Cause**: This error occurs if you try to run the program from the `parameters.txt` file instead of `main.py`.
   - **Solution**: Make sure you are in the `main.py` file when you press the **Run** button.

