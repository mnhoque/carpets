# carpets
package assignment_1;
import java.io.IOException;


public class Car {
	
	static int distance;                                         // distance to object on right side : 1) distance=-1 --> when the car is already parked  2)distance=0 --> no parking space detected  3)distance=1 --> when parking space detected
	static int position_after;  
	static int position_before;
	static int detected=0;                                       //  if detected=0 --> means no parking place,  if detected=1 --> means  parking place found
	static boolean isParked;	
	int max = 500;                                               
    static	int US1,  US2, IR1,  IR2;

    
	// ###########################################################################
/// first: it checks if the car is parked, if not it check if it detects free parking space, if not it checks if the car within the street, that is, 0-495
	public int[]  moveForward( ) {
		
	 if(isParked){System.out.println("isParked");
	       position_after =position_before;		 }
	 else if(detected==1){
		 System.out.println("detected=1");
		 position_after =position_before;	
	}
	 else if(position_before < 0 || position_before >= max){
		 position_after =position_before;	
		 System.out.println("position_before < 0  OR     position_before >=max");	 }
	 
	 else if(position_before >= 0 && position_before < max){ // this else if has the same influence as the next else if
		 position_after = position_before +1;	
		 System.out.println("0<=  position  < max"); }
	 
	

	 else {
		 		 System.out.println("invalid input"); 

	 }	
	 int[]Move={position_after,detected};
	 return Move;
	}
	
	// ###########################################################################
	//  this method return an int which represent the distance to the right object of the car.
	public int isEmpty(int us1,int us2) { 
		
		if(isParked==true){
			return distance= -1;                       // if car is already parked, return distance =-1
		}						
		if(isParked==false) {                               // if not parked so we have two cases 1-detect 2- no detect
										
			    for (int i = 0; i < 5; i++) {             // take input values 5 times and get// average to avoid the noisy.
			    	if(us1>= 0 && us1 <= 200){
			    	    US1 += us1/5;
				    }
			        else{
				        US1 = 0;                             // it means the US1 data is noisy (out of range or no the US1 not working)
			        }}
			    for (int i = 0; i < 5; i++) {             // take input values 5 times and get// average to avoid the noisy.
			    	if(us2>= 0 && us2 <= 200){
			    		US2 += us2/5;
				    }
			        else{
			        	US2 = 0;                            // it means the US2 data is noisy (out of range or no the US2 not working)
			        }}
			    
			    
			     if(US1 < 100 || US2  < 100 ){ 		       // 	if it is true, it means there are no parking place available (detected)		
                    
    				
				    distance=0;                         
			        detected=0;
			        
			    }
			     else if(US1 >= 100 || US2  >= 100 ){ 		       // 	if it is true, it means there are parking place available (detected)		
	                    
	    				
					    distance=1;                         // means parking place id detected.
				        detected=1;
				      //
				       // System.out.println("?");
				    }
			    else{                                   
	   				
				      // distance=0;	                       // no parking space detected
				       System.out.println("invalid input");}
			    }
		return distance;}
	
	public int[]  moveBackward( ) {
		 if(isParked){System.out.println("isParked");
	       position_after =position_before;		 }
	
		 else if(detected==1){
			 System.out.println("detected=1");
			 position_after =position_before;		     }
		 
	     else if(position_before > 0 && position_before <= max){ 
		 position_after = position_before -1;		
		 System.out.println("position_before > 0  OR     position_before <= max");; 
}
	 
	     else if(position_before <= 0 || position_before > max){
		 position_after =position_before;
		 System.out.println("position_before <= 0  OR     position_before > max");}

	     else {
		 		 System.out.println("invalid input"); 

	 }	
	 int[]Move={position_after,detected};
	 return Move;
		
		}
	boolean Park() {
		boolean X=false;
		    if(isParked==true){System.out.println(" The Car is alredy parked");}       //case1:  if the car is already parked.
		    
		    
											
		    else if(position_before <= 0 ||position_before > max){                //case2: if the car is not in the street range (0-495)
		    	System.out.println("It can not parking. the car not in the street.");} 
		    
					
		    else if ( (position_before > 0 && position_before <= max) ) {  // case4:  if distance =1 --> parking place is detected, and the car is parking now
		    	 if(distance==1 ){
				 for (int i = 0; i < 5; i++) { // to move 5 meter forward when empty// park place is detected
				}
				 System.out.println(" it is parking...t");
				  X = true;

				 }else if (distance!=1  ) {                                              // case4:  if distance =1 --> parking place is detected, and the car is parking now
					System.out.println(" no parking place available");}
		    	 
		    	 
		    	 else{	System.out.println(" no parking place available within range");}}

		    else {System.out.println(" invalid input");}                                               //case3: if distance not equal to 1 --> it means no parking space detected yet.
		   
			
			return X;
			}
	
	
	boolean UnPark() {   
		if(isParked){		    // case1: isParked== true  --> the UnPark() returns true.
		String A= "unpark th car...";
		return true;
		}else{
			
			return  false;

		}
		
	}
	// ###########################################################################
		int[] WhereIs() {
			int x;
			if(isParked){x=0;}
			else   { x=1;  }
			
			int [] state= {position_before,x};
			return state ; 
		}
	
	public static void main(String args[]) throws IOException {

	}

}


