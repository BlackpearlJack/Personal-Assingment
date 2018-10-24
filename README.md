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

    static PreparedStatement prepareStatement(String queryl) {
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
          //Establish a connection to the database
        try{
            con =  DriverManager.getConnection(url,usrname,usrpass);
            System.out.print("Connection to database was a success");//output for successful connection to database
        }
        catch(SQLException e)
        {
            System.out.print("Connection to database failed");
            
        }
    }

          
}
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package mypersonalassignment;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;
import java.sql.*;
import java.util.logging.Level;
import java.util.logging.Logger;



/**
 *Class for the login GUI
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
     
private class al implements ActionListener{


    private void ActionPerformed( ActionEvent ae) throws SQLException, ClassNotFoundException{
        
            PreparedStatement ps;
            ResultSet rs;
            String uname = name.getText();
            String upass = String.valueOf(pass.getPassword());
            
        String queryl = "SELECT * FROM 'registationform.login'";
        
        try{
            ps = MyConnection.prepareStatement(queryl);
            
            ps.setString(1,uname);
            ps.setString(2, upass);
            
            rs = ps.executeQuery();
            
            if(rs.next())
            {    //option window to show if login is successful
                JOptionPane.showMessageDialog(null, "WELCOME");
          
            }
            else{//Option window to show if login is not successful
                JOptionPane.showMessageDialog(null, "Access Denied");
            }
        }catch(SQLException e){
            Logger.getLogger(Login_receptionist.class.getName()).log(Level.SEVERE, null,e);
        }

                                                                              
}

        @Override
        public void actionPerformed(ActionEvent ae) {
            throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        }

        private Object MyConnection() {
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
    private final JLabel Username;
    private final JTextField uname;    
    private final JLabel Adress;
    private final JTextField ad;
    private final JLabel gender;
    private final JTextField sex;
    private final JButton usernew;
    private final JButton xt;
    
    
    New_User_Class() {
        
        
    //Values Initialization    
        JFrame nuc = new JFrame("New_User_Class");
        Secondpanel = new JPanel();
        Firstname = new JLabel("Firstname: ");
        fname = new JTextField();
        fname.setColumns(21);
        Secondname = new JLabel("Secondname: ");
        sname = new JTextField();
        Username = new JLabel("Username: ");
        uname = new JTextField(11);        
        sname.setColumns(21);
        tel =new JLabel("Telephone: ");
        tele =new JTextField();
        tele.setColumns(21);
        Adress = new JLabel("Address");
        ad = new JTextField();
        ad.setColumns(20);
        gender = new JLabel("Gender");
        sex = new JTextField();
        sex.setColumns(1);
        usernew = new JButton("Create User");
        xt = new JButton("Cancel");
        
    //Output of initialized values    
        Secondpanel.add(Firstname);
        Secondpanel.add(fname);
        Secondpanel.add(Secondname);
        Secondpanel.add(sname);
        Secondpanel.add(Username);
        Secondpanel.add(uname);
        Secondpanel.add(tel);
        Secondpanel.add(tele);
        Secondpanel.add(Adress);
        Secondpanel.add(ad);
        Secondpanel.add(gender);
        Secondpanel.add(sex);
        Secondpanel.add(usernew);
        Secondpanel.add(xt);
        nuc.add(Secondpanel);
        
        
        nuc.add(Secondpanel);
        nuc.setSize(1200, 800);
        nuc.setLocationRelativeTo(null);
        nuc.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        nuc.setVisible(true);
    usernew.addActionListener(new ad());
    }
  public boolean checkUsername(String username) throws ClassNotFoundException
    {
        PreparedStatement ps;
        ResultSet rs;
        boolean checkUser = false;
        String query = "SELECT * FROM registrationform.registration WHERE Username ='?'";
        
        try {
            ps = MyConnection.prepareStatement(query);
            ps.setString(1, username);
            
            rs = ps.executeQuery();
            
            if(rs.next())
            {
                checkUser = true;
            }
        } catch (SQLException ex) {
            Logger.getLogger(New_User_Class.class.getName()).log(Level.SEVERE, null, ex);
        }
         return checkUser;
    }
    
private class ad implements ActionListener{

private void ActionPerformed( ActionEvent ea) throws SQLException, ClassNotFoundException{
    String frtname = fname.getText();
    String sndname = sname.getText();
    String usrname = uname.getText();
    String telephone = tele.getText();
    String sexa = sex.getText();
    String adress = Adress.getText();
    
   if(checkUsername(uname)){
       JOptionPane.showMessageDialog(null,"Client already exists");
   }
   else{
      
   }
   PreparedStatement pv;
   String queryx ="INSERT INTO registrationform.registration (`Firstname`, `Lastname`, `Telephone`, `Adress`, `Gender`, `Username`)VALUES ('?', '?', '?', '?', '?', '?')";

   try{
       pv = MyConnection.prepareStatement(queryx);
       
       pv.setString(1,frtname);
       pv.setString(2,sndname);
       pv.setString(3,usrname);
       pv.setString(4,telephone);
       pv.setString(5,sexa);
       pv.setString(5,adress);
   }catch(SQLException ne){
     Logger.getLogger(New_User_Class.class.getName()).log(Level.SEVERE, null, ne);  
       
   }
}    

        @Override
        public void actionPerformed(ActionEvent ae) {
            throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        }
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
              
        new Login_receptionist();
       
    }
    
}
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package mypersonalassignment;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

/**
 *
 * @author Lester
 */
public class Home_Page {
    private final  JButton adu;
    private final  JButton lg;
Home_Page(){ 
    JFrame hpg = new JFrame("Home_Page");
    JPanel cod = new JPanel();
    adu = new JButton("Add User");
    lg = new JButton("Logout");
    
    cod.add(adu);
    cod.add(lg);    
    hpg.add(cod);
    
    hpg.setSize(1200, 800);
    hpg.setLocationRelativeTo(null);
    hpg.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    hpg.setVisible(true);
    
    adu.addActionListener(new home());
    lg.addActionListener(new out());
}
private class home implements ActionListener{
    private void ActionPerformed(ActionEvent he){
        new New_User_Class();
    }

        @Override
        public void actionPerformed(ActionEvent ae) {
            throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        }
    }
private class out implements ActionListener{
    private void ActionPerformed(ActionEvent ut){
        new Login_receptionist();
    }

        @Override
        public void actionPerformed(ActionEvent ae) {
            throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        }
    }
}

