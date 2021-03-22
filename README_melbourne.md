# Starbucks_Capstone
Starbucks Capstone Challenge

## Quick overview
The main challenge of this project is to "learn from the past" regading which has been the most successful offer for a particular profile of user that will be determined by a decision tree model using, as features, demographics and average transaction amount.  
The Introduction in the jupyter notebook and the blog in https://medium.com/@eva-marchetti/learning-from-customers-response-to-offers-ed7553e0b931 will explain the challenge in more details
## How to run the jupiter notebook
The whole notebook is based on three datastes provided by Starbucks and available in this repository in the zip file
- portfolio.json
- profile.json
- transcript.json

You will need to extract and save the files in the zip file.  
Then, in the first code cell in the jupiter notebook (Importing the necessary libraries and files), particularly in the code:  
  
portfolio = pd.read_json('data/portfolio.json', orient='records', lines=True)  
profile = pd.read_json('data/profile.json', orient='records', lines=True)  
transcript = pd.read_json('data/transcript.json', orient='records', lines=True)  
<br>
You need to make sure that the path to the json files is aligned with the path in your enviroment for the code to actually find the files.  
<br>
Since we are importing json files, you may need to update your pandas version in order to read json file correctly.  
If you need to do so, from a jupyter notebook workspace, you can go to the terminal and run the command conda update pandas before reading in the files.  
You can see how to access the terminal and how the install works using the two images below. First you need to access the terminal:  
![Terminal](/image/pic1.png)

Then you will want to run the above command:  
![command](/image/pic2.png)

Finally, when you enter back into the notebook (use the jupyter icon again), you should be able to import the json files correctly.
