# Lab Report 3: Researching commands

In this report, I'll be reseaching the command `grep`

## Command 1: `grep -a`

According to the `--help` output, `grep -a` should output the files that are binary-ily equivalent.


Below is the first example: 


![image](https://user-images.githubusercontent.com/122564073/221623139-7f034f84-c889-4404-a3f3-83f9b22466f7.png)


Here I was looking for all the instances where any word in any file was binary-ily equivalent to `yes`. It shows that there are 106 lines that are equivalent.
However, I don't think I ran the command correctly because when I scroll through the grep results without `wc`, all the lines had "yes" in the line. I was expecting
some "yes" but not all "yes". My working theory is that, `grep -a` looks for any word containing "yes" as words like "yesterday" and "eyes" came up, which aren't 
binary-ily equivalent to "yes". 


I tried `grep -a` with "no" and the results are more or less the same. I scrolled through all the results and it was the same. There were words containing "no" such as
"another".

![image](https://user-images.githubusercontent.com/122564073/221659488-245e48f6-1b7b-440b-8b5f-9f1663e18e29.png)


## Command 2: `grep -o`


According to the `--help`, `grep -o` will output the only the part of the line matching the pattern. In the image below, it shows in which file "travel" is found. Some
files contain "travel" multiple times. 


![image](https://user-images.githubusercontent.com/122564073/221661399-834c6212-1272-4fe1-a060-3548276fe8bb.png)


Same thing happens when I search for "mad"


![image](https://user-images.githubusercontent.com/122564073/221664140-676e0240-83c5-4884-83f6-b5b81774eb86.png)


## Command 3: `grep -w`


According to the `--help`, `grep -w` selects only those lines containing matches that form whole words. First example below is searching for "ocean".


![image](https://user-images.githubusercontent.com/122564073/221674445-a1fcf3d8-7d1c-4a4d-8af6-4c673874d2a2.png)


I wanted to try "yes" again to see if the results were any different from the example earlier. I think that the results will be different. There will be less results
because there are only so many situations in which one can say "yes" in a travel guide.


![image](https://user-images.githubusercontent.com/122564073/221677866-778daa40-c59e-451e-b4f0-0d6340f45442.png)


And I was right, the results were different. The results contained only when "yes" was a whole word instead of in a word.


## Command 4: `grep -i`


According to the `--help`, `grep -i` will output the results of the search pattern ignoring case. So I tried it with "yes" and the results were about the same as the
earlier examples. 


![image](https://user-images.githubusercontent.com/122564073/221680609-7a396f4b-9a62-4103-8a00-102fe38538c5.png)


Once again, I searched "mAn" and yes, the case was ignored, and grep outputed all the instances of which "mAn" occurred.


![image](https://user-images.githubusercontent.com/122564073/221681240-87e5581e-e9b4-49c6-9f66-88e01e24a836.png)

