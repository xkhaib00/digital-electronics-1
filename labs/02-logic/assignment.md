# Lab 2: KHAIBULLIN Rishat

### 2-bit comparator

1. Karnaugh maps for other two functions:

   Greater than:

   ![K-maps](1.png)

   Less than:

   ![K-maps](2.png)

2. Equations of simplified SoP (Sum of the Products) form of the "greater than" function and simplified PoS (Product of the Sums) form of the "less than" function.

   ![Logic functions](3.png)

### 4-bit comparator

1. Listing of VHDL stimulus process from testbench file (`testbench.vhd`) with at least one assert (use BCD codes of your student ID digits as input combinations). Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   Last two digits of my student ID: **195589**

```vhdl
     p_stimulus : process
 begin
     -- Report a note at the beginning of stimulus process
     report "Stimulus process started" severity note;

     -- First test case ...
     s_b <= "00"; 
     s_a <= "01"; 
     wait for 100 ns;
     -- ... and its expected outputs
     assert ((s_B_greater_A = '0') and
             (s_B_equals_A  = '0') and
             (s_B_less_A    = '1'))
     -- If false, then report an error
     -- If true, then do not report anything
     report "Input combination 00, 00 FAILED" severity error;


     -- WRITE OTHER TEST CASES HERE


     -- Report a note at the end of stimulus process
     report "Stimulus process finished" severity note;
     wait; -- Data generation process is suspended forever
 end process p_stimulus;
```

2. Text console screenshot during your simulation, including reports.

   ![your figure](4.png)

3. Link to your public EDA Playground example:

   [https://www.edaplayground.com/...](https://www.edaplayground.com/x/PBD3)
