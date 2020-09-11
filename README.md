# Itinerary-Planner
Hadoop, Java, Sentiment analysis,  Google Map API, AJAX, MYSQL


Pre-Requisites
1) Download Tomcat from http://tomcat.apache.org/download-70.cgi and download the 32/64 bit core Windows zip file.\
2) Downlad the MySQL Installer and Workbench from http://dev.mysql.com/downloads/windows/ and install it.
3) Please set the MySQL username = 'root' and password = 'root'
4) Set up the MySQL server to run on port 3306. 

NOTE - Any deviation from the above constraints will not allow you to run the program successfully.

=================================================================

There are 2 ways to run the program
	a) 	Run the sample output we have directly on the tomcat server to view the results
	b)	Follow each and every step to arrive at the data from sratch and then run the server to view the results.
	
	Let us look at both method in detail. You can choose however you want it to run. Run the sample data or build the data and then run it.
	
	a)	Run the sample output we have directly on the tomcat server to view the results
	
		1)	Extract the tomcat zip file we downloaded in first step to your desired destination in Pre-Requisites step 1.
		2)	Goto the Database/ folder and open SampleData.sql in MySQL workbench you downloaded in Pre-Requisites step 2.
		3)	After the file is opened RUN the file in workbench and the database will be created.
		4)	Goto the /Web_Servlet folder and copy TravelItinerary.war and paste it in the apache-tomcat-7.0.57/webapps folder of Tomcat folder 
			you extracted in step 1.
		5)	Set the JAVA_HOME as the jdk source path in Enviornment variables and JRE_HOME as the jre source path in Enviornment vairables.
		6)	Open cmd.exe as admin and goto the Tomcat source folder.
		7)	Goto \apache-tomcat-7.0.57\bin\ folder and run "startup.bat". 
		8)	After doing this the website will be loaded and you can view the Web Project by going to http://localhost:8080/TravelItinerary/Driver
		9)	The website is setup. You can now go ahead and explore it.
		
	b)	Follow each and every step to arrive at the data from sratch and then run the server to view ther results.
		
		>	Run Hadoop
			1)	Goto the \Pre-Processing folder and copy and paste the entire Hadoop folder on your CCR.
			2)	The "/input" folder in Hadoop contains the data to be processed. This data is a colllection of reviews of businesses from 2 states.
			3) 	Run the slurm file $sbatch SLURM_MyHadoop
			4) 	After the job is completed, $cd output_wordcount
			5)	All the 16 files are output of parallel processing
		
		>	Process the Hadoop Results
			1)	After the data is processed and we have the results, we now have to parse the data and calculate the score and store it into 
				the	database.
			2) 	Copy all the output files from /output_wordcount/ from the CCR job you ran to "/Pre-Processing/ParseHadoopFiles/processedFiles/".
			3)	Now all the output files are pasted onto the local system on "/Pre-Processing/ParseHadoopFiles/processedFiles/".
			4)	Now RUN the "ParseHadoopFiles.jar" file in "/Pre-Processing/ParseHadoopFiles/" folder by typing 
				"java -jar ParseHadoopFiles.jar" in cmd.
			5) Doing this will Process all the Hadoop Output Files and put it in the database for the Web Project to use.
			
		>	Running the Web Server
			1)	Extract the tomcat zip file we downloaded in first step to your desired destination in Pre-Requisites step 1.
			2)	Goto the Database/ folder and open SampleData.sql in MySQL workbench you downloaded in Pre-Requisites step 2.
			3)	After the file is opened RUN the file in workbench and the database will be created.
			4)	Goto the /Web_Servlet folder and copy TravelItinerary.war and paste it in the apache-tomcat-7.0.57/webapps folder of Tomcat folder 
				you extracted in step 1.
			5)	Set the JAVA_HOME as the jdk source path in Enviornment variables and JRE_HOME as the jre source path in Enviornment vairables.
			6)	Open cmd.exe as admin and goto the Tomcat source folder.
			7)	Goto \apache-tomcat-7.0.57\bin\ folder and run "startup.bat". 
			8)	After doing this the website will be loaded and you can view the Web Project by going to http://localhost:8080/TravelItinerary/Driver
			9)	The website is setup. You can now go ahead and explore it.

