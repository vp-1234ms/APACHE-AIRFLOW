# APACHE-AIRFLOW

![AIRFLOW](https://github.com/user-attachments/assets/7b003ed2-7a9f-479b-943d-89852c50161d)

![AIRFLOW1](https://github.com/user-attachments/assets/4435c2ae-bf2d-49ad-9a54-c2764d88461b)

![AIRFLOW2](https://github.com/user-attachments/assets/5edaa87b-970f-4059-93aa-305585b81c8c)

![AIRFLOW3](https://github.com/user-attachments/assets/c69803ab-3849-4d28-a9bb-33e5fa5e8773)





APACHE AIRFLOW IS POWERFUL DATA ORCHESTRATION TOOL
DATA ORCHESTRATION -> AUTOMATING THE FLOW OF DATA ACROSS VARIOUS SYSTEMS WHICH ENSURES DATA IS EFFECTIVELY COLECTED, PROCESSED, TRANFORMED AND MADE AVAILABLE FOR FURTHER ANALYSIS.

APACHE AIRFLOW BASIC TERMINOLOGIES:
1) DAG(DIRECTED ACYCLIC GRAPH): DAG IS COLLECTION OF YOUR TASKS AND REPRESENTS STRUCTURE OF YOUR WORKFLOW
2) TASK: IT IS UNIT OF WORK DONE IN DAG.
3) OPERATOR: IT IS USED TO HANDLE TASK WITHIN DAG.
4) SCHEDULER: IT MONITORS THE DAG AND ENSURE EACH TASK RUN WHEN THEY ARE SUPPOSED TO.

EG:
AT END OF THE DAY COMPANY WANTS TO:
> EXTRACT DATA FROM VARIOUS SOURCES: DATABASE(POSTGRESQL), API, CSV FILES.
> TRANFORM THE DATA BY CLEANING AND COMBINING IT.
> LOAD THE DATA INTO DATA WAREHOUSE(EG: GOOGLE BIG QUERY OR AWS REDSHIFT)
> GENERATE DAILY REPORT AND MAIL IT TO MANAGEMENT


1) DAG:
HERE ENTIRE RPOCESS 
EXTRACT -> TRANFORM -> LOAD -> GENERATE
THIS ENTRIRE WORKFLOW IS DEFINED AS DAG
THIS DAG REPRESENT ENTIRE DATA PIPELINE WHICH WILL RUN DAILY.
2) TASK:
HERE EACH UNIT OF DAG IS CALLED TASK
EG: 
EXTRACT DATA FROM POSTGRESQL -> TASK1, EXTRACT DATA FROM API -> TASK2, EXTRACT DATA FROM CSV -> TASK3
TRANSFORM DATA -> TASK4
LOAD DATA -> TASK5
GENERATE REPORT AND SEND IT VIA MAIL -> TASK6
3) OPERATOR: 
EACH TASK IS A DAG IS DEFINED USING OPERATOR. OPRATOR DDEFINE WHAT EACH TASK WILL DO.
EG:
PostgresOperator: FOR EXTRACTING DATA FROM POSTGRES
HttpOperator: FOR CALLING AN API TO GET DATA.
Python Operator: FOR DATA TRANSFORMATION STEP.
BigQueryOperator: FOR LOADING DATA INTO BIG QUERY
EmailOperator: FOR SENDING THE FINAL REPORT VIA EMAIL




SO NOW TWITTER DATA PIPELINE USING AIRFLOW:

1) ACESING TWITER DATA USING TWITTER API:
GENERATING API KEY, AND ACCCESS TOKEN

SO NOW CREATING twitter_etl.py:
Which will collect tweets of desired username using twitter api
SO WE WILL GET TWEETS IN LIST FORMAT ALPNG WITH OTHER IMAGE DATA AND OTHER RAW DATA

SO NOW WE HAVE COLLECTED DATA FROM TWITTER.
SO NOW WE HAVE TO PROCESS AND TRANFROM INTO STRUCTURED AND ONLY HAVEE REQUIRED DATA -> BASCIALLY CLEAN DATA OR TRANSFORM DATA

SO NOW IN SAME FILE WE WILL CREATE LIST WHICH WILL HAVE EACH TWEETS: USERNAME, TWEET TEXT, LIKES, RETWEET COUNT , AND TIME CREATED.
CONVERTING THIS LIST TO DATAFRAME AND STORING IT AS CSV FILE.




2) CREATING EC2 INSTANCE:
WE WILL CREATE EC2 ISTANCE FOR LAUNCHING APACHE AIRFLOW
ONCE WE CERATE THIS EC2 INSTACNE DOWNLOAD THE EC2 KEY AND COPY SSH KEY TO CONNECT TOT HIS INSTANCE USING CMD.

INSTALLING REQUIRED DEPENDECING ON EC2 INSTANCE LIKE PYTHON3, APACHE AIRFLOW, PANDAS, S3FS, TWEEPY

3) RUNNING APACHE AIRFLOW SERVER:
SO NOW USNG APAHCE STANDALONE COMMAND IN CMD TO RUN ENTIRE AIRFKOW SERVER
IT WILL PROVIDE USERNAME AND PASSWORD 

SO NOW GO TO EC2 INSTANCE COPY PUBLIC DNS AND ADD OUR 8080 PORT AND PASTE IT ON WEB BROWSER AND HIT ENTER 

NOTE: AFTER PASTING THIS URL YOU MAY NOT ABLE TO SEE ANYTHING THIS WILL BE DUE TO RESTRICTED TRAFFIC
SO FOR THIS GO TO SECURTY GROUPS AND SELECT ALL TRAFFIC AND IP ACEES ANYWHERE (THIS IS NOT GOOD PRACTICE BUT SAKE OF PROJECT AND LEARNING WE CAN DO AL TRAFFIC ACCESS)

SO NOW ON CLCIKING ENTER WILL SEE AIRFLOW CONSOLE WHICH WILLL ASK FOR USERNAME AND PASSWORD WHICH WE GOT INTIALLY ON CMD

SO NOW WE WILL SEE OUR DAGS AND OUR TASKS DONE SO FOR FOR APACHE AIFLOW ON THIS PAGE


4) CREATING S3 BUCKET:
THIS WILL BE USED TO STORE TWITTER DATA CSV FILE
SO NOW CRETING twitter_dag.py
THIS WILL STORE OUR DATA ONTOS3 BUCKET

5) UPLOADING OUR BOTH twitter_etl.py AND twitter_dag.py ONTO EC2 MACHINE:
SO NOW CREATE ONE MORE EC2 CONNECTIONIN NEW CMD WINDOW USING EC2 SSSH KEY
NOW CREATING twitter_etl.py FILE IN AND PASTE THE CODE AND SAVE THE CHNAGES SIMILARY FO FOR twitter.day.py CREATE NEW FILE AND PASTE THE CODE AND SAVE THE CHANGES

SO NOW WE WILL SEE THIS FILES ONTO OUR AIRFLOW CONSOLE ON WEB BROSER

6) REVIEING DAG CRETED ON WEB BROSER AIRFLOW CONSOLE:
HERE WE CAN SEE OUR UPLOADED CODE AND THEN RUN IT. SO WE WILL SEE IT'S STAUS IN GRAPH SECTION.

THERE MIGHT BE CHANCE IT FAILING CAUZE WE HAVE NOT GIVEN PERMISSION TO EC2 TO ACCESS OR WRITE DATA ON S3 BUCKET FOR THIS WE NEED TO CREATE IAM ROLE.
SO THIS IAM ROLE WILL CONNECT EC2 AND S3 BUCKET WE USING OR EC2 WIL GET ACCESS TO S3 BUCKET WHERE WE WANT TO WRITE DATA.

SO NOW AGAIN RUNNING OUR CODE ON APACHE AIRFLOW. NOW WE CAN CHECK LOGS IT WILL MARK SUCCESS
AND EVENTUALLY WE CAN SEE OUR CSV FILE OF TWITTER STORED ON AWS S3 BUCKET.



 






