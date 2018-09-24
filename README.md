# Personal-Assingment
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package example;

import java.awt.*;
import javax.swing.*;



/**
 *
 * @author Lester
 */
public class GUI extends JFrame//Login Class for the program
{
     private final JLabel nl;
     private final JPanel mp;
     private final JTextField name;
     private final JLabel pl;
     private final JPasswordField pass;
     
     GUI()
     { 
         
        JFrame mf = new JFrame("Login");
        mp = new JPanel();
        nl = new JLabel("Username: ");
        name = new JTextField();
        name.setColumns(21);
        pl = new JLabel("Password: ");
        pass = new JPasswordField(21);
        JButton ln = new JButton("Login");
        JButton cl = new JButton("Clear");
        
        
        mp.setLayout(new FlowLayout(FlowLayout.CENTER));
        mp.add(nl);
        mp.add(name);
        mp.add(pl);
        mp.add(pass);
        mp.add(ln);
        mp.add(cl);
        mf.add(mp);
        
        add(mp);
        setSize(1200, 300);
        setLocationRelativeTo(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout(FlowLayout.LEFT));
        setResizable(false);
        setVisible(true);
       
    }
    
}
//MAIN CLASS TO OUTPUT THE PROGRAM
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package example;





/**
 *
 * @author Lester
 */
public class PersonalAssignment{
/**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
              
        new GUI();
       
    }
    
}
