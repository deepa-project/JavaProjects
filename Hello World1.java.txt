import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

import javax.annotation.processing.FilerException;
public class HelloWorld1 {
	static void myMethod() {
	    System.out.println("I just got executed!");
	  }
	static void createFile(String str) throws IOException {
		
		System.out.println("Hello "+str);
		File myObj1=new File(str+".txt");
		try {
			File myObj=new File(str+".txt");
			if (myObj.createNewFile()) {
				System.out.println("File Created:"+myObj.getName());
			}else {
				System.out.println("File already exists.");
			}
		}
		catch(FilerException e){
			System.out.println("An error occured");
			e.printStackTrace();			
		}
	}//end of method CreateFile
	
	static void write2File(String filename,String str) throws IOException {
		try {
		      FileWriter myWriter = new FileWriter(filename);
		      BufferedWriter bw=new BufferedWriter(myWriter);
		      bw.append(str);
		      bw.close();
		      myWriter.close();
		      System.out.println("Successfully wrote to the file.");
		    } catch (IOException e) {
		      System.out.println("An error occurred.");
		      e.printStackTrace();
		    }
		
	}//end of write2File
	
	static void readFile(String filename) throws IOException {
		File myObj=new File(filename);
		Scanner myReader=new Scanner(myObj);
		while (myReader.hasNextLine()){
			String data=myReader.nextLine();
			System.out.println(data);
		}
		myReader.close();
		
		
		
		
	}//end of readFile
	static void menu() throws IOException {
		System.out.println("Enter the number against the name:");
		System.out.println("1.Alice");
	
		System.out.println("2.Bob");
		System.out.println("3.Charlie");
		System.out.println("/n");
		Scanner myObj=new Scanner(System.in);
		int myNumber=myObj.nextInt();
		System.out.println("You entered "+myNumber);
		switch(myNumber) {
		case 1:
			System.out.println("User requesting access to Alice's user permissions");
			System.out.println("Alice has permissions to read from her wall, write to her wall");
			System.out.println("Enter 1 to read from your wall");
			System.out.println("Enter 2 to write to your wall");
			System.out.println("Enter 3 to reaf Bob's wall");
			//System.out.println("Enter 4 to exit");
				
			Scanner AliceObj=new Scanner(System.in);
			int AliceNumber=AliceObj.nextInt();
			switch(AliceNumber)
			{
			case 1:
				try {
					readFile("Alice.txt");
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				menu();
				break;
			case 2:
				System.out.println("Enter text to write to your wall");
				Scanner myObj1 = new Scanner(System.in);  // Create a Scanner object
			   

			    String str = myObj1.nextLine();  // Read user input
			    write2File("Alice.txt",str);
			    write2File("Charlie.txt",str);
			    menu();
				break;
			case 3:
				try {
					readFile("Bob.txt");
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				
				menu();
				break;
			
				
			default:
				menu();	
						}
			
			break;
		case 2:
			System.out.println("User requesting access to Bob's user permissions");
			System.out.println("I assume you are Bob!");
			System.out.println("Enter 1 to read from your wall");
			System.out.println("Enter 2 to write to your wall");
			Scanner BobObj=new Scanner(System.in);
			int BobNumber=BobObj.nextInt();
			switch(BobNumber)
			{
			case 1:
				try {
					readFile("Bob.txt");
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				menu();
				break;
			case 2:
				System.out.println("Enter text to write to your wall");
				Scanner myObj2 = new Scanner(System.in);  // Create a Scanner object
			   

			    String str = myObj2.nextLine();  // Read user input
			    write2File("Bob.txt",str);
			    write2File("Charlie.txt",str);
			    menu();
				break;
						
				
			default:
				menu();	
						}
			
			
			break;
		case 3:
			System.out.println("User requesting access to Charlie's user permissions");
			System.out.println("I assume you are Charlie!");
			System.out.println("Enter 1 to read from your wall");
			System.out.println("Enter 2 to write to your wall");
			Scanner CharlieObj=new Scanner(System.in);
			int CharlieNumber=CharlieObj.nextInt();
			switch(CharlieNumber)
			{
			case 1:
				try {
					readFile("Charlie.txt");
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				menu();
				break;
			case 2:
				System.out.println("Enter text to write to your wall");
				Scanner myObj3 = new Scanner(System.in);  // Create a Scanner object
			   

			    String str = myObj3.nextLine();  // Read user input
			    //write2File("Bob.txt",str);
			    write2File("Charlie.txt",str);
			    menu();
				break;
						
				
			default:
				menu();	
						}
			
			break;
		
		default:
			menu();
		}
	}

	public static void main(String[] args) throws IOException {
		// TODO Auto-generated method stub
		String[] filenames= {"Alice","Bob","Charlie"};
		System.out.println("Hello World!");
		
		myMethod();
		
		createFile("Deepa3");
		for(int i=0;i<filenames.length;i++)
		{
			createFile(filenames[i]);
			
		}
		write2File("Alice.txt","Hi Alice!");
		readFile("Alice.txt");
		menu();
	}

}
