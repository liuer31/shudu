import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
public class Sudoku extends JFrame{
	 private JPanel[] pnlGame;
	 private JTextField[][][] txtGame;
	 public Sudoku() {
	 pnlGame = new JPanel[12];
	 txtGame = new JTextField[9][3][3];
	 gridInit();
	 }
	 public void gridInit() {
	 this.setDefaultCloseOperation(this.EXIT_ON_CLOSE);
	 this.setSize(400, 300);
	 this.setResizable(false);
	 this.setTitle("Suduko");
	 this.setLayout(new GridLayout(3, 4)); //set layout
	 for (int i = 0; i < 12; i++) {
		 if((i+1)%4!=0) {
	 pnlGame[i] = new JPanel();
	 pnlGame[i].setBorder(BorderFactory.createLineBorder(Color.black)); // use border to draw the grid
	 pnlGame[i].setLayout(new GridLayout(3, 3));
	 this.add(pnlGame[i]);}
		 else if(i==3) {
			 JButton btn1=new JButton("新游戏"); //Create JButton object
			 btn1.addActionListener(new ActionListener() {
			 @Override
			 public void actionPerformed(ActionEvent e) {
				 System.out.print("新游戏"); 
			 }
			 });
			 pnlGame[i] = new JPanel();
			 pnlGame[i].add(btn1);
			 this.add(pnlGame[i]);
		 }
		 else if(i==7) {
			 JButton btn2=new JButton("提示"); //Create JButton object
			 btn2.addActionListener(new ActionListener() {
			 @Override
			 public void actionPerformed(ActionEvent e) {
				 System.out.print("tishi"); 
			 }
			 });
			 pnlGame[i] = new JPanel();
			 pnlGame[i].add(btn2);
			 this.add(pnlGame[i]);
		 }
		 else {
			 JButton btn3=new JButton("cundang"); //Create JButton object
			 btn3.addActionListener(new ActionListener() {
			 @Override
			 public void actionPerformed(ActionEvent e) {
				 System.out.print("cundanag"); 
			 }
			 });
			 pnlGame[i] = new JPanel();
			 pnlGame[i].add(btn3);
			 this.add(pnlGame[i]);
		 }
	 }
	 
	 //填数独
	 int t=0;
	 for (int z = 0; z < 9; z++) {
		 if((z+1+t)%4==0) t++;
	 for (int x = 0; x < 3; x++) {
	 for (int y = 0; y < 3; y++) {
	 txtGame[z][x][y] = new JTextField();
	 txtGame[z][x][y].setBorder(BorderFactory.createEtchedBorder());
	 txtGame[z][x][y].setFont(new Font("Dialog", Font.ITALIC, 20));// Set size and font
	 txtGame[z][x][y].setHorizontalAlignment(JTextField.CENTER);// set position
	 pnlGame[z+t].add(txtGame[z][x][y]);
	 }
	 }
	 }
	 for (int z = 0; z < 3; z++) {
		 for (int x = 0; x < 3; x++) {
		 for (int y = 0; y < 3; y++) {
		 txtGame[z][x][y].setText((int)(Math.random()*10) + "");
		 txtGame[z][x][y].setEditable(false);
		 }
		 }
		 }
		 this.setVisible(true);
		 }
		 public static void main(String[] args) {
		 new Sudoku();
		 } }
