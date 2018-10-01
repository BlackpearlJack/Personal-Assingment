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
     private final JCheckBox check;
     
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
        check = new JCheckBox("Remember Password");
                
        
        mp.setLayout(new FlowLayout(FlowLayout.CENTER));
        mp.add(nl);
        mp.add(name);
        mp.add(pl);
        mp.add(pass);
        mp.add(ln);
        mp.add(check);
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
/* My Connection class to connectthe databse using j connector
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package example;

import java.sql.*;
import com.mysql.jdbc.Driver;


/**
 *
 * @author Lester
 */
public class MyConnection {

    static PreparedStatement preparestatement(String select__from_login_WHERE_UsernameMax_AND_) {
        throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
    }

  //Values Initialization and declaration
    private Connection con = null;
    private String query1 = null;
    private ResultSet rs;
    private final String url=("jdbc:mysql://localhost:3306/registrationform");
    private final String usrname = "root";
    private final String usrpass = "";
    
    //Function to connect with mysql database
    public MyConnection(){
      
        try{
            //Establish connection
            Class.forName("com.mysql.cj.jdbc.Driver");
           System.out.print("Connection attained");//connection to driver successful
                               
        } catch (Exception e)
        {
            System.out.print("Connection Error");//Output if connection to driver fails          
        }
        try{
            con = (Connection) DriverManager.getConnection(url,usrname,usrpass);
            System.out.print("Connection to database was a success");//output for successful connection to database
        }
        catch(SQLException e)
        {
            System.out.print("Connection to database failed");
            
        }
    }

          
}




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
