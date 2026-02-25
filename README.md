<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name: ARAVIND L. S.              </h3>
<h3>Register Number: 212224060022      </h3>
<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>
<h3>Procedure:</h3>
Input and Output
<br>Input:
This algorithm will take three words.
<br> B A S E<br>
    B A L L<br>
           ----------<br>
           G A M E S<br>

Output:
It will show which letter holds which number from 0 – 9.
For this case it is like this.

              B A S E                         2 4 6 1
              B A L L                         2 4 5 5
             ---------                       ---------
            G A M E S                       0 4 9 1 6
Algorithm
For this problem, we will define a node, which contains a letter and its corresponding values.<br>

isValid(nodeList, count, word1, word2, word3)<br>

Input − A list of nodes, the number of elements in the node list and three words.<br>

Output − True if the sum of the value for word1 and word2 is same as word3 value.<br>

Begin<br>
   m := 1<br>
   for each letter i from right to left of word1, do<br>
      ch := word1[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>
      val1 := val1 + (m * nodeList[j].value)<br>
      m := m * 10<br>
   done<br>

   m := 1<br>
   for each letter i from right to left of word2, do<br>
      ch := word2[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val2 := val2 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   m := 1<br>
   for each letter i from right to left of word3, do<br>
      ch := word3[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val3 := val3 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   if val3 = (val1 + val2), then<br>
      return true<br>
   return false<br>
End<br>
<hr>
<h2>Sample Input and Output:</h2>
SEND = 9567<br>
MORE = 1085<br>
<hr>
MONEY = 10652<br>
<hr>
<h2>Program:</h2>

```
import itertools

def solve_cryptarithm(word1, word2, word3):
    letters = set(word1 + word2 + word3)
    
    if len(letters) > 10:
        print("Too many unique letters (max 10 allowed).")
        return
    
    letters = list(letters)
    
    for perm in itertools.permutations(range(10), len(letters)):
        letter_digit = dict(zip(letters, perm))
        
        if (letter_digit[word1[0]] == 0 or
            letter_digit[word2[0]] == 0 or
            letter_digit[word3[0]] == 0):
            continue
        
        num1 = int("".join(str(letter_digit[ch]) for ch in word1))
        num2 = int("".join(str(letter_digit[ch]) for ch in word2))
        num3 = int("".join(str(letter_digit[ch]) for ch in word3))
        
        if num1 + num2 == num3:
            print("Solution Found:")
            print(f"{word1} = {num1}")
            print(f"{word2} = {num2}")
            print(f"{word3} = {num3}")
            print("\nLetter Mapping:")
            for k in sorted(letter_digit):
                print(k, "=", letter_digit[k])
            return
    
    print("No solution found.")

word1 = input("Enter first word: ").upper()
word2 = input("Enter second word: ").upper()
word3 = input("Enter result word: ").upper()

solve_cryptarithm(word1, word2, word3)
```
<h2>Output:</h2>
<img width="871" height="525" alt="image" src="https://github.com/user-attachments/assets/3cbc2f65-0711-40f9-bcee-4a9261852ab7" />

<h2>Result:</h2>
<p> Thus a Cryptarithmetic Problem was solved using Python successfully</p>
