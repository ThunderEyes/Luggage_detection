# Abandoned luggage detection in complex environments (Team Work Project)

This project consists of detecting some luggages that may be abandoned in different kinds of places. This is a project done during my academic period with a team of 6 members.

## Explaination of the project

This project is composed of 3 steps.

¤ The first one is the luggage detection. We detect some baggages through furnished videos, and to better process the future interactions of the luggages the persons who are 
the nearest from them. The detection is done by a perception library : YOLO. 
Why ? This project had to be done in only 3 months composed of one day of work per week. We did'nt have time to build a huge database of luggages that could be used to train
neural networks. In fact, we just began to learn machine learning and deep learning at this time, so I would be difficult to apply unconsistent knowledge. The lack of time has 
forced us to leverage an already trained model to detect luggages.

¤ The second one, the luggage re-identification. We need to track the movements of the baggages over time to know what's going on. For this task, it's important to know to who
belong a baggage. It's for this reason we decided to store all the important data in a database. We used a database tool name MongoDB. 
How it works ? At each frame, some calculations are done to evaluate the position of the luggage and the nearest person, and some associations are done. All the informations are
stored in the database.

¤ And finally, the last step is to launch an alarm when a luggage is considered as abandoned. A certain amount of time is deduced from the frames, and then we call the alarm 
when the luggage is over a threshold distance from his owner (the first nearest person).

## System algorithm
 ### Database
 
 <img width="368" alt="image" src="https://github.com/user-attachments/assets/8235af7c-07bf-4b21-af00-3beecd09e222"> <br>
 The database is composed of three relations: humans, suitcases, associations.
 The humans and the suitcases are identified by an id (track_id) and a class which corresponds to the number of the item class of the YOLO model (class_id).
 The other informations identifying the humans and the suitcases are the coordinates and the frame. <br>
 <img width="386" alt="image" src="https://github.com/user-attachments/assets/e9c2f240-0af0-4fcd-9b5a-cfca2b2757dc"> <br>
 Then, we need to merge all the informations on suitcases and their owners. So, we create an association.
 <img width="301" alt="image" src="https://github.com/user-attachments/assets/a1b03cc4-c9b5-408b-971c-2315159e3e54"> <br>

 ### Alert System
 To avoid some occlusions of the luggages, we decided to implement two alert levels. The first one is activated when a suitcase seems abandoned : "To verify". The second,
 when it seems abandoned some time after the first alert "Abandoned". <br>

 <img width="355" alt="image" src="https://github.com/user-attachments/assets/024646aa-96ad-4f78-9a06-735971ad9fa6"> <br>




