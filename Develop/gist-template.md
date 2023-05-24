# Email Validation Using Regular Expresions (Regex)

Many online activities, such as ecommerce and cloud file storage applications, require that certain pieces of information be obtained through user input. There are some pieces of information that users provide that need to be checked against information stored in a database, such as a username or password. This type of information can be checked using the strict equality operator ('==='). This is a useful method to check that usernames and passwords match exactly what is expected to verify that the appropriate user is logging in to the account. There are other instances where information needs to be obtained from the user that follows a set of rules but does not need to be strictly equal to information stored elsewhere. An example of this is creating a new user for an online platform such as Facebook. Usernames need to match a specific set of rules to ensure that usernames are not vulgar or otherwise innapropriate, meet requirements for minimum and maximum lengths, have the correct character types in them, etc. This is where regular expressions are used. They compare a given piece of data, usually but not necessarily a string, against a predetermined set of rules and accept or reject input based on whether or not it meets requirements.

## Summary

The following is an example of a regex designed to ensure that a valid email address has been provided: ^(?i)[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$.  This regex ensures that the piece of data provided contains at least one alphanumeric character or permissable special character that is followed by an '@' symbol, a domain name and a top level domain that is at least two characters long. Depending on the code in which it's used, information about why a piece of data passed or failed the regex can be provided to the user. It should be noted that this method of email verification does not check to ensure that the provided email address is active. It only checks that the provided address meets these requirements. 

The remainder of this document provides a detailed explanation of each component of the regex above.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
Regular expressions use anchors to denote where the provided data must match with the requirements of the regex. The carat "^" at the beginning of the email checker regex indicates that the provided email address must meet requirements beginning at the very start of the string. The '$' at the end of the expression requires that the matching pattern ends when the string ends. This ensures that the email address being checked is the only data being provide. It couldn't be part of a longer sentence, for example. Other anchor types that are not used in this example can require matching at the first character only, last character only, anytime before the last character or under other conditions. 

### Quantifiers
Quantifiers in regular expressions indicate how many times the pattern determined by the regex can or must repeat. The "+" in the email checker regex requires that each piece of data entered must match an uppercase or lowercase letter of the alphabet or the numbers 0-9 or the characters '._%+-'  at least once, with no upper limit, before the provided data reaches the '@' symbol. There are other quantifiers that are not listed in this code. There is one represented by '*' that matches given patterns 0 or more times which makes that pattern optional but able to be repeated infinitely. The quantifier represented by '{n}' requires that a given pattern be matched n times. The quantifier represented by '?' matches a given pattern zero or one times. There are even more quantifiers of varrying technical complexity.

### OR Operator
The example provided in the Summary section does not contain any explicit OR operators, which would be represented by the '|' symbol. However, when a group of characters are presented as acceptable matches within a set of brackets, it can be considered an implicit OR operator. This is because when [a-z] is provided as a possible pattern or match, it is not read as 'a match can be any of the provided characters.' It's instead read as 'a match can be a or b or c or d...' However, the explicit OR operator can allow for different sets of possible matches to be considered acceptable. 

### Character Classes
Regular expression character classes allow groups of characters to be identified which input data will be checked against at specific locations. In the email verifier above, there are three instances where character classes are used. The first is '[a-z0-9._%+-]'. This character class allows for input data characters before the '@' symbol to be the letters a-z (uppercase or lowercase), the numbers 0-9, or the symbols '._%+_'. The second case occurs after the '@' symbol and is written [a-z0-9.-]. This allows input data characters after the '@' symbol but before the '.' to be the letters a-z (uppercase or lowercase), the numbers 0-9, or the symbols '.' or '-'. The third occurence comes after the '.' and is written [a-z] and allows input data to include the letters a-z after the '.'. 

### Flags
Flags in regular expression change how different parts of the expression are interpreted. In the example above, the (?i) flag tells the expression not to differentiate between uppercase and lowercase letters in the following character class. It essentially tells the regex not to be case sensitive. Other flags used in regular expressions include 'g' which makes the regex global and allows it to search entire provided strings for matching patterns, 'm' will alter the behavior of '^' and '$' anchors making them operative at the start and end of each line of data provided instead of operative at the beginning and end of the total provided data. 

### Grouping and Capturing
Grouping and capturing in regular expressions are done by enclosing parts of the code in '()'. There are no instances of grouping and capturing in the email validator example above, the parenthesis are used to apply the ?i flag only. In general, a piece of code in a regular expression grouped inside of parentheses will look for instances within the provided data that matches the grouped code. Capturing is a natural byproduct of grouping as the matches found within provided data will be marked or 'captured' for later reference or use. 

### Bracket Expressions
Bracket expression in regex code are used to define character classes, which have been explained above. Each character class in the email validator regex example is enclosed inside brackets.

### Greedy and Lazy Match
Greedy and lazy matching in regular expressions determines how characters in provided data will be matched. A 'greedy' match will look for any and all matches to a predefined pattern inside of input data. A 'lazy' match will simply look for at least one occurrence. In the above regex, there is greedy matching before and after the '@' symbol as well as after the '.'. This is because those expressions will check every piece of data provided to it to ensure that it conforms to the established pattern. A lazy match would only check that at least one match is found in each section of the provided data. There is not symbol being used to explicitly tell the regex to use greedy matching. 

### Boundaries
Boundaries in regular expressions are the limits to which the regex will be applied. In the e-mail validator example, the boundaries are set by the '^' and '$' symbols indicating that matching must begin at the start of the provided data and will end at the end of the provided data. There are instances where matching would begin after the start of provided data and stop before the data's end. 

### Back-references
Back reference in regular expressions use previously captured data (explained above) as reference points to check sections of input data past the point where the initial data was captured. There are no back references used in the email validator example. However, a back reference could be used to ensure that input data at a specific location matches data that was captured previously by grouping. 

### Look-ahead and Look-behind
A look-ahead assertion in regular expressions is called by including '(?=...) in the expression. It searches ahead in the provided data for matching patterns defined by the expression but does not return any data. It only checks for the presence of a given pattern. Look-behind assertions work similarly but check behind the current position of a regex in a provided data set. 

## Author

Hello, my name is Brian Morse. I was an Arabic Cryptologic Linguist in the Marine Corps, a child abuse investigator in California and Oregon, and an Army Reserves Mortuary Affairs Specialist. I have a degree in Psychology and am currently attending the University of Oregon coding bootcamp.

Over the years, I have gained valuable experience in different fields, from the military to social work. I have developed a strong sense of adaptability, a sharp eye for detail, and a unique problem-solving skillset. As a child abuse investigator and foster resource home certifier, I honed my communication, interpersonal, and organizational skills, as well as my ability to work under pressure and in sensitive situations.

Now, I am excited to pursue a career in web development as a full stack web developer. I am eager to use my skills and experience to develop innovative solutions and put my shoulder to the wheel to achieve group goals. I am a quick learner, a team player, and a hard worker. I am committed to continuously improving my skills and knowledge in this dynamic and ever-changing field.

I'm am always looking to improve my skills and am open to any and all suggestions. If you have feedback, encouragement, advice, or criticism, please provide it to me by using my contact information below. Thank you for coming by and have an excellent day.

Please contact me via email at Brian.P.Morse@gmail.com with any tips or other feedback. My github profile can be viewed at: https://github.com/BrianMorse1.
