# Jogchat_kafka_service
This is a mircroservice providing abilities to create, get, subscribe to company, edu topics

GET   /kafka/company/
Input: String in S&P500/Unicorn company name (e.g. intuit, uber)
output: True/False
Description: get whether company topic already exsits

GET   /kafka/edu/
Input: String in edu name (illinois, stanford)
output: True/False
Description: get whether edu topic already exsits

POST /kafka/company/broadcast
Input: JSON typed:
{
  company:"uber",
  msg:"这是想在群里说的话",
  user: "chaoran@uber.com",
  timestamp: $TIMESTAMP
}
Return:True/False
Description: 广播msg

POST /kafka/edu/broadcast
Input: JSON typed:
{
  edu:"illinois",
  msg:"这是想在群里说的话"
  user: "chaoran@illinois.edu",
  timestamp: $TIMESTAMP
}
Return:True/False
Description: 广播msg

POST /kafka/company/subscribe
Input: JSON typed:
{
  company:"uber",
  username:"chaoran@uber.com"
}
Return:True/False,
Description: suberscribe company user to company topic

POST /kafka/edu/subscribe
Input: JSON typed:
{
  company:"intuit",
  username:"wang374@illinois.edu"
}
Description: suberscribe edu user to company topic



***************Push to backend microservice endpoints********************************
PUSH /kafka/company/pushmsg
Input: JSON typed:
{
  startTime:""
  endTIme:""
  company:"uber",
  username:"chaoran@uber.com"
}
Return: msgList
Description: get company msg user subscribed to 

PUSH /kafka/edu/pushmsg
Input: JSON typed:
{
  startTime:""
  endTIme:""
  company:"illinois",
  username:"wang374@uber.com"
}
*************************************************
Return: msgList
Description: get edu msg user subscribed to 





