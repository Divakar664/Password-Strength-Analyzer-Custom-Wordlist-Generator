# Password-Strength-Analyzer-Custom-Wordlist-Generator
A comprehensive Python tool for analyzing password strength and generating custom wordlists for security testing and educational purposes.
Features
🔐 Password Strength Analyzer
Industry-Standard Analysis: Uses the zxcvbn library for realistic password strength estimation
Multiple Entropy Calculations: Shannon entropy and charset-based entropy measurements
Pattern Detection: Identifies common weak patterns like sequential numbers, repeated characters, and keyboard patterns
Crack Time Estimates: Provides realistic estimates for password breaking time
User Input Awareness: Can check passwords against user-specific information to detect personalized weak passwords
📝 Custom Wordlist Generator
Personalized Inputs: Generate wordlists from names, dates, pets, keywords, places, and favorites
Leetspeak Variations: Automatic generation of common character substitutions (a→4, e→3, i→1, o→0, etc.)
Pattern-Based Generation: Adds years (1950-2029), common suffixes, and special characters
Date Format Variations: Multiple international date formats (YYYYMMDD, DD/MM/YYYY, MM-DD-YYYY, etc.)
Word Combinations: Creates permutations and combinations of input words
Case Variations: Generates uppercase, lowercase, and capitalized versions
Export to .txt: Compatible with password cracking tools like John the Ripper and Hashcat
Installation
The project uses Python 3.11 and includes the following dependencies:

zxcvbn-python - Password strength estimation
nltk - Natural language processing
tkinter - GUI framework (built-in with Python)
Dependencies are managed automatically via the Replit environment.

Usage
GUI Mode (Recommended)
Launch the graphical interface:

python main.py
or explicitly:

python main.py --gui
The GUI provides two tabs:

Password Analyzer Tab: Enter a password to get detailed strength analysis
Wordlist Generator Tab: Input user information to generate custom wordlists
CLI Mode
Analyze Password Strength
Basic analysis:

python main.py --cli analyze --password "MyP@ssw0rd123"
With user-specific inputs:

python main.py --cli analyze --password "MyP@ssw0rd" --user-inputs "john,smith,fluffy"
JSON output format:

python main.py --cli analyze --password "test123" --json
Generate Custom Wordlist
Basic wordlist generation:

python main.py --cli generate --names "john,jane" --dates "19900515" --pets "fluffy" --output wordlist.txt
With multiple input types:

python main.py --cli generate \
  --names "alice,bob" \
  --dates "20000101,19951225" \
  --pets "buddy,max" \
  --places "boston,newyork" \
  --keywords "password,admin" \
  --output targeted_wordlist.txt
With statistics:

python main.py --cli generate \
  --names "john" \
  --dates "19900515" \
  --output wordlist.txt \
  --stats
Password Analysis Output
The analyzer provides comprehensive feedback including:

Overall Strength Score: 0-4 rating (Very Weak to Very Strong)
Shannon Entropy: Information-theoretic measure of randomness
Charset Entropy: Entropy based on character set complexity
Crack Time Estimates: Multiple estimation methods
Pattern Detection: Identified weak patterns
Security Feedback: Warnings and suggestions for improvement
Example output:

============================================================
PASSWORD STRENGTH ANALYSIS REPORT
============================================================
Password: ********
Length: 8 characters
Overall Strength: Fair (2/4)
ENTROPY ANALYSIS:
  Shannon Entropy: 22.45 bits
  Charset Entropy: 47.63 bits
CRACK TIME ESTIMATES:
  zxcvbn estimate: 3 hours
  Charset-based: 2 days
  Guesses needed: 10^6.2
PATTERNS DETECTED:
  - Word Then Numbers
SECURITY FEEDBACK:
  Warning: This is similar to a commonly used password
  - Add another word or two
  - Avoid sequences
============================================================
Wordlist Generation Process
The generator applies multiple transformation techniques:

Base Variations: Case transformations (UPPER, lower, Capitalize)
Leetspeak: Character substitutions (a→4/@, e→3, i→1/!, o→0, s→5/$, t→7, etc.)
Common Suffixes: Numbers (123, 1234, 12345) and symbols (!, !!, @, #, $)
Years: Historical and recent years (1950-2029)
Combinations: Permutations of input words with various separators
Date Formats: Multiple international format variations
Reversals: Reversed strings and duplications
Example transformations for input "john":

john
John
JOHN
j0hn
J0hn
john123
John123
john2024
john!
john@
john#
nhoj (reversed)
johnjohn
Wordlist Statistics
Generated wordlists include statistics:

Total Entries: Number of generated passwords
Unique Entries: Number of unique passwords
Average Length: Mean password length
Length Range: Minimum and maximum password lengths
Security & Ethical Use
This tool is designed for:

✅ Educational purposes
✅ Security testing of your own systems
✅ Password strength awareness
✅ Authorized penetration testing
Important: Only use this tool on systems you own or have explicit permission to test. Unauthorized access to computer systems is illegal.

Project Structure
.
├── main.py                  # Main entry point
├── password_analyzer.py     # Password analysis module
├── wordlist_generator.py    # Wordlist generation module
├── cli.py                   # Command-line interface
├── gui.py                   # Tkinter GUI interface
├── README.md               # This file
├── replit.md               # Project documentation
└── pyproject.toml          # Python project configuration
Technical Details
Password Strength Scoring
The tool uses multiple methods to assess password strength:

zxcvbn Algorithm: Realistic password strength estimation that considers:

Common password patterns
Dictionary words
Spatial patterns on keyboards
Repetition and sequences
Date patterns
Shannon Entropy: Measures the randomness/unpredictability of the password

Charset Entropy: Calculates entropy based on character set diversity:

Lowercase letters: +26 possibilities
Uppercase letters: +26 possibilities
Numbers: +10 possibilities
Special characters: +32 possibilities
Pattern Detection
The analyzer detects:

Sequential numbers (012, 123, 234, etc.)
Repeated characters (aaa, 111, etc.)
Keyboard patterns (qwerty, asdf, etc.)
Single case passwords (all upper or all lower)
Word-then-numbers pattern (password123)
Examples
Example 1: Analyze Your Password
python main.py --cli analyze --password "MySecureP@ssw0rd2024"
Example 2: Generate Targeted Wordlist
python main.py --cli generate \
  --names "alice,bob,charlie" \
  --dates "19900101,19851015" \
  --pets "fluffy,buddy,max" \
  --keywords "company,admin,secure" \
  --output company_wordlist.txt \
  --stats
Example 3: Test Password Against User Info
python main.py --cli analyze \
  --password "Alice1990!" \
  --user-inputs "alice,bob,1990,fluffy"
License
This project is provided for educational and ethical security testing purposes only.

Contributing
This is an educational project. Feel free to extend it with additional features such as:

More pattern transformations
Dictionary attack simulation
Password generation recommendations
Batch processing capabilities
Additional export formats
Author
Created as a security education and password testing tool.
