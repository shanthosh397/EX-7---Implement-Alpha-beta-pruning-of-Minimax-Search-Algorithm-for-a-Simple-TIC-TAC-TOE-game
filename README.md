<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: Shanthosh G   </h3>
<h3>Register Number: 2305003008         </h3>
<H3>AIM:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm:</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION:</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm:</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning:</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance

## PROGRAM:
```python
import math

b = [" "] * 9
w = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]

def show():
    print(f"\n{b[0]}|{b[1]}|{b[2]}\n-+-+-\n{b[3]}|{b[4]}|{b[5]}\n-+-+-\n{b[6]}|{b[7]}|{b[8]}\n")

def win():
    for x,y,z in w:
        if b[x]==b[y]==b[z]!=" ": return b[x]
    return "Draw" if " " not in b else None

def abp(maxp, alpha, beta):
    r = win()
    if r=="O": return 1
    if r=="X": return -1
    if r=="Draw": return 0

    if maxp:
        best = -math.inf
        for i in range(9):
            if b[i]==" ":
                b[i]="O"
                best = max(best, abp(False, alpha, beta))
                b[i]=" "
                alpha = max(alpha, best)
                if beta <= alpha: break
        return best
    else:
        best = math.inf
        for i in range(9):
            if b[i]==" ":
                b[i]="X"
                best = min(best, abp(True, alpha, beta))
                b[i]=" "
                beta = min(beta, best)
                if beta <= alpha: break
        return best

def move():
    best, mv = -math.inf, None
    for i in range(9):
        if b[i]==" ":
            b[i]="O"
            sc = abp(False, -math.inf, math.inf)
            b[i]=" "
            if sc > best: best, mv = sc, i
    return mv

print("Tic Tac Toe (You:X  Computer:O)")
show()

while True:
    try:
        p = int(input("Enter position (1-9): "))-1
        if b[p]!=" ": print("Taken!"); continue
    except: print("Invalid!"); continue

    b[p]="X"; show()
    if win(): break

    print("Computer thinking...")
    b[move()]="O"; show()
    if win(): break

r = win()
print("Draw!" if r=="Draw" else f"{r} wins!")
```
<hr>
<h2>INPUT AND OUTPUT:</h2>

<img width="1036" height="711" alt="image" src="https://github.com/user-attachments/assets/d25e1cde-5989-41a5-a61e-68189bc9e3e5" />

<img width="902" height="688" alt="image" src="https://github.com/user-attachments/assets/2625e27b-d13e-484e-b91c-45f0bbfda2e7" />

<img width="1059" height="715" alt="image" src="https://github.com/user-attachments/assets/a8dc9f96-a8a4-466c-b48b-21322d611d79" />

<img width="947" height="276" alt="image" src="https://github.com/user-attachments/assets/c4001294-8f03-42d1-95d5-32a83f89bf30" />




## RESULT:
We have successfully implemented Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game.
