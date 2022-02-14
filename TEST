library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity nand_nor_top is
    Port ( A1 : in  STD_LOGIC;      -- NAND gate input 1
           A2 : in  STD_LOGIC;      -- NAND gate input 2
           X1 : out  STD_LOGIC;     -- NAND gate output
           B1 : in  STD_LOGIC;      -- NOR gate input 1
           B2 : in  STD_LOGIC;      -- NOR gate input 2
           Y1 : out  STD_LOGIC);    -- NOR gate output
end nand_nor_top;

architecture Behavioral of nand_nor_top is
begin
X1 <= A1 nand A2;    -- 2 input NAND gate
Y1 <= B1 nor B2;     -- 2 input NOR gate
end Behavioral;
