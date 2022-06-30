# Dashboarding_F1
Data preparation workflow (using Alteryx) and some dashboards made using Tableau. Visualizing prosperous sponsor cases for a sponsor about to enter Formula 1. The other dashboard is an interactive resume, also made using Tableau.

The topic of this project was the proposal of potentially valuable sponsorships in Formula 1
motor racing based on the teams’ and drivers’ performance across the years using data
visualization tools. The main problem that needed to be solved, was whether without more
specific data regarding other sponsorship’s cost dependencies would we be able to still produce
valuable insights and propose set of constructors and drivers. We decided to develop two
dashboards – one for constructors and one for drivers, so that the comparison analysis could be
conducted more easily. We operated on the dataset downloaded from renowned data analysis
platform Kaggle.com, we cleaned the data using Alteryx and employed Tableau as our main
data visualization tool. The performed data analysis let us deduct, that although talent is an
extremely important thing, it is the car that is possibly the most important factor of Formula 1
success. Moreover, we discovered the positive relation between driver’s performance and
social media engagement of his fanbase, that is additionally boosted when driver is of young
age. This enabled us to propose George Russell and Lando Norris as potential valuable
beneficiaries of a sponsorship and McLaren as a prosperous team.

We have provided a relationship schema to illustrate
the used data as if it was a database. This is done to give the reader of this report an overview
of how the data in this assignment are connected and to provide some motivation for the
operations in the Data preparation/ cleaning chapter.
![image](https://user-images.githubusercontent.com/64472833/176758162-102d510b-7072-409d-8a9d-5b647d0e65b5.png)

The result of the data preparation/ cleaning process are the transformed data that was used to
make the dashboard visualization in Tableau. Since Tableau as a tool is made for visualization
and not for data preparation/ cleaning, we have utilized Alteryx Designer for this purpose.
Moreover, these tools work well together, utilizing both means that we can exploit both the
tools’ strengths, without having to limit ourselves by their weaknesses (Mathewson, 2013). The
goal with this process is to end up with as tidy data (Wickham, 2014) as possible to limit the
amount of computing power required by Tableau when the dashboard is being used. The
cleaning process results in two sets of CSV files, one used for the drivers dashboard and the
other for the constructors. CSV files have been chosen as output format since it is a common
way to store tables which most software are used to handle. An alternative could be outputting
the tables as a DBMS (Database Management System). Although this would provide better
computing speed, we have opted with CSV files due to the nature of the data (small in size,
and does not need to be accessed quickly) and the fact that new raw data is available between
large intervals (about every other week in season) and not in real time. Furthermore, the focus
of this assignment is on the ETL process rather than databases.
Throughout the data cleaning in Alteryx all data fields are treated as Strings (stored as
V_String) unless stated otherwise. Id-fields are treated as Integers and stored as Int16s.

<img align="center" img width="400" height="400" alt="image" src="https://user-images.githubusercontent.com/64472833/176758334-6b65ae8a-ebff-4509-9327-e0737796ff6b.png">

The first challenge of the raw data was the logic of the raceId. We wanted a more intuitive
structure and decided to reorganize the data in a chronological order, therefore creating a new
id field (new_raceId). This was done by sorting the selected data from the races file (raceId,
year, name, and date) by ascending date and creating a new value for every row (using
Alteryx’s Record ID). raceId was then deselected before this data was outputted into a new
CSV file (races_new_raceId). The other data was updated by selecting the relevant fields
before joining to races on raceId, and then selecting new_raceId and deselecting raceId, finally
being outputted as new CSV files. The only files to undergo more changes in the initial process
was results and races. As for results a modified status and statusId was added from the status
file. The original data distinguished a driver finishing the race from one finishing the race +n
laps down. This was changed so that a driver that had finished +4 laps down, and had a statusId
of 14, now had status as Finished and a statusId of 1. For the races file, we changed
name_of_race, removing “Grand Prix” from the fields, then changing the name of the column 
to Grand Prix. In addition, one value (United States West Grand Prix) required manual
manipulation. The operations were done in a formula field with the following code:

<img align="center" img width="400" height="400" alt="image" src="https://user-images.githubusercontent.com/64472833/176758569-ecf882c5-c626-472b-b93a-0d89e7b927cd.png">

The drivers’ dashboard consists of qualifying- and race data. The distinction is made due to the
fact that records of qualifying started later than races.
3.2.3. Common process

<img align="center" img width="400" height="200" alt="image" src="https://user-images.githubusercontent.com/64472833/176758634-ae51bc66-47c6-4b46-acd3-c3bbf2815d6c.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758763-f47cf33b-e674-4f82-aa50-d85464e58f78.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758829-7f0e055b-c500-4612-9979-68ee527cd33a.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758884-6bf1fb39-1828-4d47-a92e-0049b0cc1f8f.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758932-0f28b1b2-36f5-4536-a181-76b5d3e4745a.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758974-624d1a03-d101-43d7-9f59-e5d0b1b745ca.png">

<img align="center" img width="400" height="300" alt="image" src="https://user-images.githubusercontent.com/64472833/176758994-1e718f0b-14c0-4ac6-8c74-a53ac3e2b02b.png">






