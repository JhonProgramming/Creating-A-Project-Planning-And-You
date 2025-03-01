# Creating-A-Project-Planning-And-You
---------------------------------------------------------------------------------------
Planning A New Project:
When creating a project plan, add a cover page, use headers and bullet points and add a contents page / table to aid readbility
Be consistent with headers
Watch your SPAG
Make it all relevent to the project you are designing
---------------------------------------------------------------------------------------
Part A - Project Proposal:
---------------------------------------------------------------------------------------
Business Context:
SWOT analysis of project
Naming + explanation of stakeholders in project
---------------------------------------------------------------------------------------
Requirements:
list of requirement name, brief description, essential or desirable
Functional requirements (what program needs to do)
Non-functional requirements (not features but things it needs, e.g security & speed)
decomposition of requirements (in depth explanation of how they work / how they will be implemented)
----------------------------------------------------------------------------------------
Key Performance Indicators And Use Cases:
KPIs (list KPIs and give a small explanation, KPIs = things you can use to judge performance e.g number of bug reports or time spent on a screen)
User acceptance criteria (list and give a small explanation, user acceptance = what the user expects to be able to do with the program e.g log into an account)
Use cases (short examples of a task and the steps that a user would take to do it)
----------------------------------------------------------------------------------------
Description Of Proposed Solution:
A short paragraph giving an explanation of the project and what it aims to achieve
----------------------------------------------------------------------------------------
Risks And Risk Mitigation:
Give risks relevant to the specfic project as well as general ones
Risks - give examples and explanations of risks to the developement / success of the project
Risk mitigation - give examples and explanations of how these specific risks will be mitigated
-----------------------------------------------------------------------------------------
Regulations, Legal And Ethics:
Laws & Legislations:
give exampels of diferent laws and legislations and how they are relevant to the project
give general digital ones like GDPR but also ones specific to the project like health laws for a health app
Ethical Considerations:
give different ethical considerations around the project (e.g ethics of giving out health advice) as well as ideas on how to deal with them
-----------------------------------------------------------------------------------------
Appendix:
add the appendix of research done (not sure on this still)
-----------------------------------------------------------------------------------------
Other Stuff:
Discuss how the planned project will meet industry standards and the use of emerging technologies
----------------------------------------------------------------------------------------
Part B - The Design:
----------------------------------------------------------------------------------------
Visual / Interface Design:
wireframes of each of the main pages of the solution 
can use figma, conva or other similar tools
use comments and labels to help better explain
make design good
use whitespace
use visual hierarchy?
-----------------------------------------------------------------------------------------
Algorithms:
Use both flowcharts and pseudocode to create some of the main systems from the program
do a good few
include error handling and stuff
dont make it too technical (dont use a load of technical terms or make it like code or anything)
----------------------------------------------------------------------------------------
Data Requirements:
Entity Relationship Diagram - diagram that does the database design
Data flow diagram - diagram of how the data flows between different parts and processes of the program (level 0/1)
Use case diagram - diagram with different users of the system and what they can do (add an explanation bit underneath)
Data dictionary - table outlining the variables used in the ERD, what they are for, their data type, length, error handling etc
-----------------------------------------------------------------------------------------
Test Strategy/Plan:
List all the components of the progam to be tested
list the prerequesites and dependencies needed to test each part
list the different types of testing that will be done (e.g security, funcitonality, integrating testing)
give brief description of the tests done for each test type (e.g functionality testing is check input validation, check error handling, etc)
-------------------------------------------------------------------------------------------

Part B - Creating The Prototype:

-------------------------------------------------------------------------------------------
general stuff: 
coding the program
need to follow the plan but do need to strictly stick to it
2 languages (c# & SQL)
interface good
include good  comments
use lots of error handling
use input / data validation
keep namimg conventions simple, short and relevant
use functions and classes where possible
------------------------------------------------------------------------------------------
programming notes:
-----------------------------------------------------------------------------------------
SQL:
sql connection string:
string connectionString = "Data Source = (LocalDB)\\MSSQLLocalDB; AttachDbFilename = file path ; Integrated Security = True; Connect Timeout = 30"; 
SqlConnection sqlConnection = new SqlConnection(connectionString);
sql command:
SqlCommand command = new SqlCommand("command name", sqlConnection); 
command.CommandType = CommandType.StoredProcedure; 
passing paramters to sql command:
command.Parameters.AddWithValue("@parameter", variable);
using insert, update, delete commads:
sqlConnection.Open(); 
command.ExecuteNonQuery(); 
sqlConnection.Close(); 
using select command (putting it into datatable):
SqlDataAdapter sd = new SqlDataAdapter(cmd);
sqlConnection.Open(); 
sd.Fill(datatable name); 
sqlConnection.Close(); 
stored procedures:
Create procedure [dbo].[procedure name] 
( 
@param1 type, 
@param2 type 
) 
as 
begin 
sql command
End 
insert:
insert into table name values @param1, @param2 
select:
select * from table name (where____ if neccessary)
delete:
Delete from table name (where___ if neccessary) 
update:
Update table name 
set column=@param1, 
column=@param2 
(where___ if neccessary)
---------------------------------------------------------------------------------------------
APIs:
private const string API_KEY = " API KEY HERE";
string Url = "http://api.openweathermap.org/data/2.5/forecast?" (<--- replace with API site url) + "q=" + city (<-- parameters) + "&mode=xml&units=metric&APPID=" + API_KEY;
getting data from API:
            // Get the response string from the URL. 
             (function-->)GetForecast(**client.DownloadString(ForecastUrl)** (<-- important bit)); 
        } 
        
        // Display the forecast. 
        private void GetForecast(string xml) 
        { 
            // Load the response into an XML document. 
            XmlDocument xmlDoc = new XmlDocument(); 
            xmlDoc.LoadXml(xml);  (<--- putting data from API into xml document)

              foreach (XmlNode timeNode in xmlDoc.SelectNodes("//time (API header thing)")) 
            { 
                // Get the time in UTC. 
                DateTime time = DateTime.Parse(timeNode.Attributes["from"].Value); 
                // Get the temperature. 
                XmlNode tempNode = timeNode.SelectSingleNode("temperature (subsection of each data entry)");
                string temp = tempNode.Attributes["value"].Value; (<--- specific bit of data from subsection)
                // Get the temperature. 
                XmlNode windSpeedNode = timeNode.SelectSingleNode("windSpeed"); 
                string windSpeed = windSpeedNode.Attributes["mps"].Value; 
---------------------------------------------------------------------------------------------
general:
empty text box:
txtPeople.Text = string.Empty; 
getting rows from datatable:
foreach (DataRow dr in datatablename.Rows) 
datatype variablename = (cast data type)(dr["column name"]); - regular get from datatable
string variable = dr["column"] != DBNull.Value ? (string)(dr["column"]) : "N/A"; - conditional get from datatable (gets data, if column for that row is blank, sets it as "N/A")
make sure to do anything with the data in the foreach loop
