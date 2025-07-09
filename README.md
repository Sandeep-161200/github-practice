When a function finishes, it needs to return back to the place it was called from. That return address is stored in LR.

Example:
assembly
Copy
Edit
BL myFunction   ; Branch and Link – saves next instruction address in LR
`
myFunction:
   ; Do something
   MOV PC, LR   ; Return to the saved address (like RET)
📌 3. Program Counter (PC / R15)
➤ What is it?
The Program Counter holds the address of the current instruction being executed.

➤ What does it do?
Automatically moves to the next instruction after every clock cycle

Can be modified manually to perform jumps, branches, or function calls

🧠 Example:
assembly
Copy
Edit
MOV PC, R1     ; Jump to the address stored in R1 (used in function pointers)
🔁 How They Work Together (Function Call Example)
assembly
Copy
Edit
main:
    BL func         ; Branch to func, save return address in LR

func:
    PUSH {LR}       ; Save return address on the stack
    ; Do some work
    POP {LR}        ; Restore LR
    BX LR           ; Branch back to return address (return to main)
Register	Action
SP	Keeps track of stack memory
LR	Remembers where to return
PC	Tells which instruction to run next

✅ Summary
Register	Full Name	Role
SP (R13)	Stack Pointer	Points to top of the stack
LR (R14)	Link Register	Holds return address after function call
PC (R15)	Program Counter	Points to the current instruction

Let me know if you’d like a diagram or visual flow of how a function call works using SP, LR, and PC!








You said:
explain about CPU registers


ChatGPT said:
Sure! Let's clearly understand CPU registers — what they are, what types there are, and how they are used (especially in ARM architecture).

🧠 What are CPU Registers?
CPU registers are small, ultra-fast memory locations inside the CPU used to store data temporarily during program execution.

They hold:

Data

Addresses

Instructions

Control/status flags

Registers are faster than RAM, because they are part of the processor itself.

📦 Types of CPU Registers (General Categories)
Type	Purpose
General-Purpose Registers	Store temporary data, variables, results
Special-Purpose Registers	Control execution (like PC, SP, LR, status flags)
Control Registers	Hold status/control flags (e.g., CPSR in ARM)
Floating-Point Registers	Handle decimal/floating-point operations (e.g., VFP/NEON in ARM)
