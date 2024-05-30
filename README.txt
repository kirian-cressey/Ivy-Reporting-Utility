README - ivy_reporting.py

Invoke on command line by running $python3 ivy_reporting.py or simply $./ivy_reporting.py.
Will produce a report file, ivy_log.csv in the directory from which this script is invoked. 

ivy_reporting.py takes as input a .csv file and assumes the following columns of data in the following order:

Chat ID, Chat Start Time, Chat Length, Buttons Clicked, Messages to Bot, Bot Responses (Generative), Bot Responses (Retrieval), Bot Responses (Low Confidence), Bot Responses (No Confidence), Attempt to Connect to Live Person, Connection Established, Conversation Rating

The first column, Chat ID, is implicit in all Data Lake Exports and is included regardless of filters applied. The other columns will need to be requested in the pull.

Any deviation from the data included or the order of the columns will result in unexpected behavior.

ivy_reporting.py will ask for location of a Data Lake file which can be specified by path during program execution. Script will preview data before outputting to a file named ivy_log.csv located in the same directory as ivy_reporting.py. Script will append data if ivy_log.csv already exists, making it easy to keep a running log. Log file will be created if it does not exist.


Definitions:

Month: An arbitrary string manually inputted by the user when adding a Data Lake pull to the log

Fiscal Year: An arbitrary string manually inputted by the user when adding a Data Lake pull to the log

Filtered: A chat which has either zero time or zero messages from user. Filtered chats are not included in any data reporting, including the Total Chats column.

Total Chats: The sum of all bot interactions that include one or more messages to the bot and last for more than zero seconds.

Total Messages from Users: The sum of all messages sent to the bot from users.

Total Button Use: Total number of times users clicked a button to interact with bot. May be multiple button pushes per chat interaction.

Total Generative Responses: Number of responses fired by the bot which use generative AI (GPT) to create an original response based on knowledge scraped from knowledge sources provided to the bot.

Total Retrieval Responses: Number of responses fired by the bot due to similarity between the user’s utterance and a pre-programmed scripted response.

Total Low-confidence Responses: Number of responses fired by the bot in which the bot asks the user “Did you mean one of the following:” 

Total No-confidence Responses: Number of responses given by the bot to indicate that no appropriate response is available to the user’s inquiry.

Accuracy Rate: [Total Generative Responses + Total Retrieval Response] / [Total
Generative Responses + Total Retrieval Response + Total Low Confidence
Responses + Total No Confidence Responses]

Resolution Rate: [Number of chats in which at least one Generative or Retrieval Response is fired, and user does not request live chat] / Total Chats

Average Rating: Exactly what you think: Sum of all rating values / number of ratings

Total Live Chat Requests: Total of chats in which a live agent was requested by the user or referred by the bot

Total Live Chat Connections: Total of chats in which a user was successfully connected to a live agent

Percentage of Chats Occurring After-Hours: Number of chats occurring outside of Service Desk hours. Note that After hours is measured by time of chat, not availability of agent.

Chats Resolved After Hours: Number of chats occurring after-hours in which at least one Generative or Retrieval Response is fired, and user does not request live chat. (Note that After hours is measured by time of chat, not availability of agent.)

After-hours Live Chat Requests: Number of times a user requests a live chat (or is referred by the bot) after hours. (Note that After hours is measured by time of chat, not availability of agent.)



