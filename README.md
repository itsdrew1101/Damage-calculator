# Damage-calculator
Wizard101 PvP Calculator - Follow comments and change the spells and their name, as well as damage where said. You can change crit and block to be more accurate for you as well as resist. Resist = Resist - pierce.
Copy paste the code into an IDE and run.
Main method: 


public class Calc
{
    public static void main(String[] args)
    {
        Calculator calc = new Calculator();
        
        //calc.printDamage();
        
        calc.setVars();
    }
    
    
Calculator Class:



import java.util.Scanner;
public class Calculator {
    Scanner input = new Scanner(System.in);
    
    
    private double spell;
    
    private double resist;
    
    private double crit;
    
    private String player = "";
    
    private String resAura = "";
    
    private String theBuffs;
    
    private double b1=0;
    
    private double b2=0;
    
    private double b3=0;
    private double b4=0;
    private double b5=0;
    private double b6=0;
    private double b7=0;
    private double b8=0;
    private double aura = 0;
    private double w1 = 0;
    private double w2 =0;
    private double w3 = 0;
    public void setVars()
    {
        System.out.println("Spell?");
        String theSpell = input.nextLine();
        if(theSpell.equals("mi"))
        {
        	//Put spell damage you want here and change mi to whatever you want (mi is minotaur)
            spell = 570;
        }
        else if(theSpell.equals("p"))
        {
        	//Same as before for rest of spells
            spell = 890;
        }
        else if(theSpell.equals("o"))
        {
            spell = 730;
        }
        else if(theSpell.equals("me"))
        {
            spell = 1000;
        }
        else if(theSpell.equals("c"))
        {
            spell = 1230;
        }
        System.out.println("Jade, Mid, Life, or Glass?");
        player += input.nextLine(); 
        if(player.equals("g"))
        {
        	//Change resist per level this is for 99 (average resist - pierce)
            resist = 0;
            crit = 1.342757937;
        }
        else if(player.equals("m"))
        {
        	//Change resist per level this is for 99 (average resist - pierce)
            resist = .12;
            crit = 1.209821429;
        }
        else if(player.equals("j"))
        {
        	//Change resist per level this is for 99 (average resist - pierce)
            resist = .27;
            crit = 1.209821429;
        }
        else if(player.equals ("l"))
        {
        	//Change resist per level this is for 99 (average resist - pierce)
            resist = .27;
            crit = 1.143353175;
        }
        System.out.println("Fortify or Brace?");
        resAura += input.nextLine();
        if(resAura.equals("f"))
        {
            resist += .15;
        }
        else if(resAura.equals("b"))
        {
            resist += .20;
        }
        System.out.println("35?");
        String check1 = input.nextLine();
        if(check1.equals("y"))
        {
            b1 = .35;
        }
        System.out.println("35?");
        String check2 = input.nextLine();
        if(check2.equals("y"))
        {
            b2 = .35;
        }
        System.out.println("35?");
        String check3 = input.nextLine();
        if(check3.equals("y"))
        {
        	//These are buffs change the 35 to whatever you want (blade bubble, traps)
            b3 = .35;
        }
        System.out.println("40?");
        String check4 = input.nextLine();
        if(check4.equals("y"))
        {
            b4 = .40;
        }
        System.out.println("40?");
        String check5 = input.nextLine();
        if(check5.equals("y"))
        {
            b5 = .40;
        }
        System.out.println("45?");
        String check6 = input.nextLine();
        if(check6.equals("y"))
        {
            b6 = .45;
        }
        System.out.println("45?");
        String check7 = input.nextLine();
        if(check7.equals("y"))
        {
            b7 = .45;
        }
        System.out.println("45?");
        String check8 = input.nextLine();
        if(check8.equals("y"))
        {
            b8 = .45;
        }
        System.out.println("25 Weakness?");
        String weakCheck1 = input.nextLine();
        if(weakCheck1.equals("y"))
        {
            w1 = .25;
        }
        System.out.println("25 Weakness?");
        String weakCheck2 = input.nextLine();
        if(weakCheck2.equals("y"))
        {
            w2 = .25;
        }
        System.out.println("30 Weakness?");
        String weakCheck3 = input.nextLine();
        if(weakCheck3.equals("y"))
        {
            w3 = .30;
        }
        System.out.println("Aura");
        String auraCheck = input.nextLine();
        if(auraCheck.equals("y"))
        {
        	//maycast auras
            aura = .25;
        }
        // 2.2654 damage is 127 damage if you want exact numbers use your damage without pet then calculate your exact pet numbers on petcalc
        double partDamage = (spell *2.2654)-(spell*2.2654*resist);
        double totalDamage1 = (partDamage) + (partDamage*b1);//+ (partDamage*b2) +(partDamage*b3) +(partDamage*b4) +(partDamage*b5)+ (partDamage*b6) +(partDamage*b7) + (partDamage*b8); 
        double totalDamage2 = (totalDamage1) + (totalDamage1*b2);
        double totalDamage3 = (totalDamage2) + (totalDamage2*b3);
        double totalDamage4 = (totalDamage3) + (totalDamage3*b4);
        double totalDamage5 = (totalDamage4) + (totalDamage4*b5);
        double totalDamage6 = (totalDamage5) + (totalDamage5*b6);
        double totalDamage7 = (totalDamage6) + (totalDamage6*b7);
        double theeTotalDamage = (totalDamage7) + (partDamage*b8);
        double weaknessTotalDamage1 = (theeTotalDamage -(theeTotalDamage *w1));
        double weaknessTotalDamage2 = (weaknessTotalDamage1 -(weaknessTotalDamage1 *w2));// - (theeTotalDamage*w2) -(theeTotalDamage*w3));
        double weaknessTotalDamagee = (weaknessTotalDamage2 -(weaknessTotalDamage2 *w3));
        double finalDamage = (weaknessTotalDamagee + (weaknessTotalDamagee*aura));
        System.out.println("Damage (no crit): " + finalDamage + " / Damage(crit) " +(finalDamage*crit));
        
        
    }
}
    

