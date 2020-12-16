# polluted-water-alert
Code Explanation

In the code, we first have to import our conf file which has all the credentials. The python json and time libraries are also imported in the same line. Since we have saved our conf file with the .py extension, we can directly import it.
import conf, json, time
json is a python library used for handling all operations on JSON objects. JSON is nothing but a data communication format widely used on the Internet for sending/receiving data between a client and server. More information on JSON can be found here. Remember, 'json' is the python library used for handling JSON objects and JSON is a data communication format. 
Now we will import Bolt python library which will let us fetch the data stored in Bolt Cloud. To send the SMS, the Sms library is also imported. The below line of code imports the required libraries.
from boltiot import Sms, Bolt
In the above line, we are importing two objects. First one is SMS which will be used to send SMS alerts and the other one is Bolt which is used for accessing data from your Bolt device like the temperature reading.
Now we will initialize two variables which will store minimum and maximum threshold value. You can initialize any minimum and maximum integer limits to them.
This would send an alert if the temperature reading goes below the minimum limit or goes above the maximum limit similar to the alerts on a polluted water.
minimum_limit = 600 
maximum_limit = 700
Now to fetch the data from Bolt Cloud, we will create an object called 'mybolt' using which you can access the data on your Bolt.
For the Bolt Cloud to identify your device, you will need to provide the API key and the Device ID when creating the mybolt object. Since the conf file holds the API key and Device ID variables, you can use them as follows,
mybolt = Bolt(conf.API_KEY, conf.DEVICE_ID)
The above code will automatically fetch your API key and Device ID that you have initialized in conf.py file.

Now to send an SMS, we will create an object of the same.
sms = Sms(conf.SID, conf.AUTH_TOKEN, conf.TO_NUMBER, conf.FROM_NUMBER)
The above code will automatically fetch your SID, AUTH_TOKEN, TO_NUMBER and FROM_NUMBER that you have initialized in conf.py file. Make sure you have given correct value in conf.py file.

Since we want to continuously monitor the  reading, we will enclose our logic to fetch, compare and send the SMS inside an infinite loop using the `while True:` statement. An infinite loop is a special loop which executes its code continuously since its exit condition is never going to be valid. To exit the loop, we will need to forcibly exit the code by holding CTRL + C
