# Personal-Assingment

//MAIN CLASS TO OUTPUT THE PROGRAM
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package mypersonalassignment;
/* My Connection class to connectthe databse using j connector
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package mypersonalassignment;

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
/*login form form for the program
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package mypersonalassignment;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;
import java.sql.*;



/**
 *
 * @author Lester
 */
public class Login_receptionist extends JFrame
//Login Class for the program
{   
     private final JLabel nl;
     private final JPanel mp;
     private final JTextField name;
     private final JLabel pl;
     private final JPasswordField pass;
     private final JCheckBox check;
     private final JButton ln;
    
     private JLabel x;

     
     Login_receptionist()
     { 
        
    //Initialize Values
        JFrame mf = new JFrame("Login");
        mp = new JPanel();
        nl = new JLabel("Username: ");
        name = new JTextField();
        name.setColumns(21);
        
        pl = new JLabel("Password: ");
        pass = new JPasswordField(21);
        
        ln = new JButton("Login");

        check = new JCheckBox("Remember Password");
           
        
        
        //Output Statements
        mp.add(nl);
        mp.add(name);
        mp.add(pl);
        mp.add(pass);
        mp.add(ln);
        mp.add(check);
        mf.add(mp);
        
        mf.setSize(800,500);
        mf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        mf.setVisible(true);
     
     ln.addActionListener(new al());
     }
     
public class al implements ActionListener{


    public void ActionPerformed( ActionEvent ae){
//Action to get data from databse after clicking login button
        if(name.getText().length()==0){//To check empty field
            JOptionPane.showMessageDialog(null,"Please fill up all fields");}
        else if(pass.getPassword().length==0){//To check empty field
            JOptionPane.showMessageDialog(null,"Please Key in Password");}
        else{
            String user = name.getText();//get input
            char[] upass= pass.getPassword();//get input
            String pwd = String.copyValueOf(upass);//converting to string from array
            if(validate_login(user,pwd)){
                JOptionPane.showMessageDialog(null,"Login Successful");
            }
            else{
                JOptionPane.showInternalMessageDialog(null,"Login Failed");
            }
        }
    } 
    private boolean validate_login(String username,String password){
        try{//Connection to database to initialize the querry
            Class.forName("com.mysql.jdbc.Driver");//MySQL Database Connection
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/registrationform","root","");
            PreparedStatement stm = conn.prepareStatement("SELECT * FROM login WHERE Username");
            stm.setString(1, username);
            stm.setString(2, password);
            ResultSet rs = stm.executeQuery();
            if(rs.next())
                return (true);
            else
                return (false);
        }
        catch(Exception e){
            e.printStackTrace();
            return false;
        }
}

        @Override
        public void actionPerformed(ActionEvent ae) {
            throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        }
    
                                                                              
}
}

/*New user Class to add new users
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package example;

import static example.MyConnection.getConnection;
import static example.MyConnection.prepareStatement;
import java.awt.event;
import java.awt.event.ActionListener;
import javax.swing.*;
import java.sql.*;
import java.util.logging.*;

/**
 *
 * @author Lester
 */
public class New_User_Class extends JFrame {
    
   
    //Declaration of values
    private final JLabel Firstname;
    private final JTextField fname;
    private final JTextField sname;
    
    private final JPanel Secondpanel;
    private final JLabel Secondname;
    private final JLabel tel;
    private final JTextField tele;
   
    
    private final JLabel Adress;
    private final JTextField ad;
    private final JButton usernew;
    private final JButton xt;
    private event.ActionListener ActionListener;
    
    New_User_Class() {
        
        
        
        JFrame nuc = new JFrame("New_User_Class");//header file
        Secondpanel = new JPanel();
        Firstname = new JLabel("Firstname: ");
        fname = new JTextField();
        fname.setColumns(21);
        Secondname = new JLabel("Secondname: ");
        sname = new JTextField();
        sname.setColumns(21);
        tel =new JLabel("Telephone: ");
        tele =new JTextField();
        tele.setColumns(21);
        Adress = new JLabel("Address");
        ad = new JTextField();
        ad.setColumns(20);
        usernew = new JButton("Create User");
        xt = new JButton("Cancel");
        
    
    
        //Function to output the values stated in the New user class window
        Secondpanel.add(Firstname);
        Secondpanel.add(fname);
        Secondpanel.add(Secondname);
        Secondpanel.add(sname);
        Secondpanel.add(tel);
        Secondpanel.add(tele);
        Secondpanel.add(Adress);
        Secondpanel.add(ad);
        Secondpanel.add(usernew);
        Secondpanel.add(xt);
        
        
        
        add(Secondpanel);
        setSize(1200, 800);// setting size of the window
        setLocationRelativeTo(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//function to close program if window is closed 
        setVisible(true);
         
    }
  
        
    }

/**
 *
 * @author Lester
 */
public class MyPersonalAssignment{
/**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
              
        new GUI();
       
    }
    
}
