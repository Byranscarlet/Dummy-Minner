//To run this code, add JDBC and Twitter4j into classpath

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.sql.*;
import java.util.Map;

import twitter4j.*;



public final class getURL {

    //DB Connection
	public static Connection getConnection() throws Exception {
		Class.forName("com.mysql.jdbc.Driver").newInstance();
		return DriverManager.getConnection("Localhost", "root","");        //add DBM info here
	}	
	



	 public static void main(String[] args) throws Exception{

		 
		 	TwitterStream twitterStream = new TwitterStreamFactory().getInstance();        

	    	Connection conn = null;
	        Statement stmt = null;
	        conn = getConnection();
	        stmt = conn.createStatement();
        
        
    		StatusListener listener = new StatusListener() {
    		  
    		  
	    		//URL filter  	
	      		String url1 = "n.pr";
	      		String url2 = "huff.to";
	      		String url3 = "npr.org";
	      		String url4 = "huffingtonpost.com";
	      		String url_tmp = null;
	      		
	    		
	    		
		        long twitterid;
		        String URL;
		        URLEntity[] URLObject;
		        User UserObject;
		        String Text;
		        HashtagEntity[] Hashtag;
		        MediaEntity[] Media;
		        UserMentionEntity[] UserMentions;
		        long IRT_user_id;
		        long IRT_status_id;
		        long RT_count;
		        long RT_id;
		        long RT_user_id;
		        String Source;
		        double Latitude;
		        double Longitude;  
		        HashtagEntity[] tmp_hashtag = null;
		            
	            
	            
	            
	            
		        @Override
		        public void onStatus(Status status) {
	               
	            	
	                URLObject = status.getURLEntities();               	
	            	
	                for (URLEntity i : URLObject) {
	                
	                	url_tmp = i.getExpandedURL().toLowerCase();
	                	
	                	
	                	if (url_tmp == url1 | url_tmp == url2 | url_tmp == url3 | url_tmp == url4) {
	                		
	                		
	                		//insert query need to be added
		                	//id
		                	twitterid = status.getId();
		                
		                	//user
		                	UserObject = status.getUser();
		
		                	//content
		                	Text = status.getText();
		                	Hashtag = status.getHashtagEntities() != null?status.getHashtagEntities():tmp_hashtag;
	
			                
			                Media = status.getMediaEntities();
			             
			                UserMentions = status.getUserMentionEntities();
			                
			                //in reply
			                IRT_user_id = status.getInReplyToUserId();
			                IRT_status_id = status.getInReplyToStatusId();
			                
			                //rt
			                RT_count = status.getRetweetCount();
			                RT_id = status.getRetweetedStatus() != null?status.getRetweetedStatus().getId():0;
			                RT_user_id = status.getRetweetedStatus() != null?status.getRetweetedStatus().getUser().getId():0;  
			                
			                //Fav_count = status.getFavoriteCount();
			                
			                //geo info
			                Latitude = status.getGeoLocation() != null?status.getGeoLocation().getLatitude():0;
			                Longitude = status.getGeoLocation() != null?status.getGeoLocation().getLongitude():0;
			                //status.getPlace().;               
			                //source
			                Source = status.getSource();
			
			                
			                //Screen info
			            	System.out.println("@" + status.getUser().getScreenName() + " - " + status.getText());
							System.out.println(status.getSource());
		                	System.out.println(Hashtag[0].getText());
		                
	                	}
	                	
	                }
	
	            }
	
	          
	            
	            
		        @Override
		        public void onDeletionNotice(StatusDeletionNotice statusDeletionNotice) {
		        	System.out.println("Got a status deletion notice id:" + statusDeletionNotice.getStatusId());
		        }
		
		        @Override
		        public void onTrackLimitationNotice(int numberOfLimitedStatuses) {
		            System.out.println("Got track limitation notice:" + numberOfLimitedStatuses);
		        }
		
		        @Override
		        public void onScrubGeo(long userId, long upToStatusId) {
		            System.out.println("Got scrub_geo event userId:" + userId + " upToStatusId:" + upToStatusId);
		        }
		
		        @Override
		        public void onStallWarning(StallWarning warning) {
		            System.out.println("Got stall warning:" + warning);
		        }
		        
		        @Override
		        public void onException(Exception ex) {
		            ex.printStackTrace();
	            }

	        
    		};
        
	        twitterStream.addListener(listener);
	        FilterQuery filter2 = new FilterQuery();
	        long[] userid = {602607781,1697640434};
	        filter2.follow(userid);
	        twitterStream.filter(filter2);

	        
	 	}
	 
}
