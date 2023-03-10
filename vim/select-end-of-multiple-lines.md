# How to break long string in vim.

### Question:
Imagine to have a line as following
```
    - "cloudwatch:*"
    - "logs:*"
    - "ec2:*"
    - "ssm:*"
    - "ec2messages:*"
```
Is there any way in vim that I can select the end of all these lines?
### Answer

Click somewhere (anywhere) in the first line you wish to append text to.

1. Press Control + V.

2. Press Down to create an arbitrary vertical block selection that spans the desired lines.

3. Press $(ctrl+4 on mac keyboard) to expand the visual block selection to the ends of every line selected.

4. Press Shift + A to append text to every selected line.

5. Type the text you want to append.

6. Press Escape and the text will be appended across the selected lines.


