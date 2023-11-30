// Andrew Rios
// 11/01/2023

/*
This class will run a simplified version of election
simulations that professional analysts run
*/
import java.util.*;
public class ElectionSimulator  {
	
	// class constants 
  public static final int NUM_DISTS = 6;
  public static final int NUM_SIMS = 5;

  public static final double PURPLE_POLL_AVG = 0.52;
  public static final double YELLOW_POLL_AVG = 1.0 - PURPLE_POLL_AVG;

  public static final double PURPLE_POLL_ERR = 0.05;
  public static final double YELLOW_POLL_ERR = -1.0 * PURPLE_POLL_ERR;

  public static final String PURPLE = "🟪";
  public static final String YELLOW = "🟡";

  public static void main(String [] args){
    Random r = new Random();
    	   	
    // introduction
    System.out.println("Welcome to the Election Simulator!");
  	System.out.println("Running " + NUM_SIMS + " simulations of " + NUM_DISTS + " districts.\n");
  	System.out.println("The Purple Party is polling at " + (PURPLE_POLL_AVG*100) + "%");
    System.out.println("The Yellow Party is polling at " + (YELLOW_POLL_AVG * 100) + "%\n");
    	
  	// the next 4 lines are to help us find the average vote percentage
  	double purpleVotePercent = 0; 
    double purpleVotePercentSum = purpleVotePercent;
  	double yellowVotePercent = 0;
  	double yellowVotePercentSum = yellowVotePercent;
    	
    // for loop to run multiple simulations
    for (int sim = 1; sim <= NUM_SIMS; sim++) {
      System.out.println("Running Simulation " + sim + ":");
  		
    	// the next 2 lines will help us generate the turn out after each simulations
    	int totalPurpleVotes = 0;
    	int totalYellowVotes = 0;
    		
    	// this loop generate each line for each district
    	for(int line = 1; line <= NUM_DISTS; line++) {
    	  System.out.print("  District #" + line + " - ");   
    		int districtTurnout = r.nextInt(1000) + 1;
    		
    		// district development    		
    		// party's vote percentage
    		double districtError = r.nextGaussian() * 0.5;
    		double percentPurpleVotes = districtError * PURPLE_POLL_ERR + PURPLE_POLL_AVG;
    		double percentYellowVotes = districtError * YELLOW_POLL_ERR + YELLOW_POLL_AVG;
    
    		// Calculating Number of Votes 
    		double numPurpleVotes = districtTurnout * percentPurpleVotes;	
    		double numYellowVotes = districtTurnout * percentYellowVotes;
        
    		// round votes and find total votes for each party
    		int roundedPurpleVotes = (int) Math.round(numPurpleVotes); 
    		totalPurpleVotes += roundedPurpleVotes; 
    		int roundedYellowVotes = (int) Math.round(numYellowVotes); 
    		totalYellowVotes += roundedYellowVotes; 
            
    		// display district results
    		System.out.print(PURPLE + " "+ roundedPurpleVotes);
    		System.out.println("  " + YELLOW + " " + roundedYellowVotes);           
    	}	

		  int totalTurnout = totalPurpleVotes + totalYellowVotes; //total votes for the simulation
    	
    	// percent and number vote received
    	purpleVotePercent = 100.0 * totalPurpleVotes / totalTurnout;
    	double roundedPurpleVotePercent = (double) Math.round(purpleVotePercent * 100) / 100; 
    	purpleVotePercentSum += purpleVotePercent;
    	
    	yellowVotePercent = 100.0 * totalYellowVotes / totalTurnout;
    	double roundedYellowVotePercent = (double) Math.round(yellowVotePercent * 100) / 100; 
    	yellowVotePercentSum += yellowVotePercent;
    	
    	// output
    	System.out.println();
    	System.out.println("  Purple Party's votes: " + totalPurpleVotes + " (" + 
		  roundedPurpleVotePercent + "%)");

    	System.out.println("  Yellow Party's votes: " + totalYellowVotes + " (" + 
		  roundedYellowVotePercent + "%)");

    	// for loop to print the emojis
    	System.out.print("  Visualization: ");
    	for (int emoji = 0; emoji < (totalPurpleVotes/100); emoji++) {
    		System.out.print(PURPLE);
    	}

		  System.out.println(); 	
    	System.out.print("                 ");
    	for (int emoji = 0; emoji < (totalYellowVotes/100); emoji++) {
    		System.out.print(YELLOW);   
    	}
    	
			System.out.println();
			System.out.println();
			System.out.println();
    }
    	
    // simulator results
    // average vote percentage for each party 
  	double purpleVotePercentAvg = purpleVotePercentSum / NUM_SIMS;
  	double finalPurpPercent = (double) Math.round(purpleVotePercentAvg * 100) / 100;
    	
    double yellowVotePercentAvg = yellowVotePercentSum / NUM_SIMS;
  	double finalYellowPercent = (double) Math.round(yellowVotePercentAvg * 100) / 100;
    	
    System.out.println("Election Simulator Results:");
    System.out.println(PURPLE + " Win = " + (finalPurpPercent >= 50.0) + " (" + 
		finalPurpPercent + "%)");
		
    System.out.println(YELLOW + " Win = " + (finalYellowPercent >= 50.0) + " (" + 
		finalYellowPercent + "%)");    	
    }
}
