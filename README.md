# TicTacToe
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package tictactoe;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

/**
 *
 * @author rohit
 */
public class TicTacToe {
    JFrame f;
    int flag=0;
    int turn=0;
    JButton b1=new JButton();  
    JButton b2=new JButton();  
    JButton b3=new JButton();  
    JButton b4=new JButton();  
    JButton b5=new JButton();  
    JButton b6=new JButton();  
    JButton b7=new JButton();  
    JButton b8=new JButton();  
    JButton b9=new JButton();
    
    TicTacToe(){  
                f=new JFrame();  
      
                  
                
                b1.addActionListener(new ButtonListener());
                b2.addActionListener(new ButtonListener());
                b3.addActionListener(new ButtonListener());
                b4.addActionListener(new ButtonListener());
                b5.addActionListener(new ButtonListener());
                b6.addActionListener(new ButtonListener());
                b7.addActionListener(new ButtonListener());
                b8.addActionListener(new ButtonListener());
                b9.addActionListener(new ButtonListener());
                
                f.add(b1);f.add(b2);f.add(b3);f.add(b4);f.add(b5);  
                f.add(b6);f.add(b7);f.add(b8);f.add(b9);  

                f.setLayout(new GridLayout(3,3));  
                //setting grid layout of 3 rows and 3 columns  

                f.setSize(300,300);  
                f.setVisible(true);
                f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                }  

    public class ButtonListener implements ActionListener {
        
        public void actionPerformed(ActionEvent e) {
            JButton b = (JButton)e.getSource();
            
            if(turn%2==0)
            {
                if(b.getText().equals(""))
                {
                    b.setText("X");
                    turn++;
                }
               
            }
            else
            {
                if(b.getText().equals(""))
                {
                    b.setText("O");
                    turn++;
                }
            }
                
                if(FinishGame()==true)
            {
                if(b.getText().equals("X"))
                {
                    JOptionPane.showMessageDialog(null,"Player 1 wins!");
                    flag=1;
                }
                else
                {
                    JOptionPane.showMessageDialog(null,"Player 2 wins!");
                    flag=1;
                }
                
            }
                if(turn==9 && flag==0)
                    JOptionPane.showMessageDialog(null,"Match Drawn");
                    
        }
    
        
        public boolean FinishGame()
        {
            if(AdjacentSelected(b1, b2) && AdjacentSelected(b2,b3))
                return true;
            else if(AdjacentSelected(b4,b5) && AdjacentSelected(b5,b6))
                return true;
            else if(AdjacentSelected(b7,b8) && AdjacentSelected(b8,b9))
                return true;
            
            
            else if(AdjacentSelected(b1,b4) && AdjacentSelected(b4,b7))
                return true;
            else if(AdjacentSelected(b2,b5) && AdjacentSelected(b5,b8))
                return true;
            else if(AdjacentSelected(b3,b6) && AdjacentSelected(b6,b9))
                return true;
            
            
            else if(AdjacentSelected(b1,b5) && AdjacentSelected(b5,b9))
                return true;
            else if(AdjacentSelected(b3,b5) && AdjacentSelected(b5,b7))
                return true;
            else
                return false;
        }
        
        public boolean AdjacentSelected(JButton a, JButton b)
        {
            if(a.getText().equals(b.getText()) && !a.getText().equals(""))
                return true;
            else
                return false;
            
        }
               
      }
    
    
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        new TicTacToe();
    }
    
}
