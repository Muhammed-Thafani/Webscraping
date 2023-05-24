import pandas as pd
import requests
from bs4 import BeautifulSoup
url='enter you url'
page=requests.get(url)
content=page.text
soup=BeautifulSoup(content)
parent_div=soup.find_all('div',{'class':'category-group'})
for cats in parent_div:
    if cats.find_all('h4')[0].text== "Job by Skill":
        box = cats.find_all('a')
        print(box[0].get('href'))
        skills_url = url+box[0].get('href')
        print(skills_url)
        page1=requests.get(skills_url)
        content1=page1.text
        soup1=BeautifulSoup(content1)
        skills_div = soup1.find_all('div',{'class':'company-directory-item'})
        l1 = [i.find('h6').text for i in skills_div]
        
    if cats.find_all('h4')[0].text== "Job by Company":
        box = cats.find_all('a')
        print(box[0].get('href'))
        skills_url = url+box[0].get('href')
        print(skills_url)
        page1=requests.get(skills_url)
        content1=page1.text
        soup1=BeautifulSoup(content1)
        skills_div = soup1.find_all('div',{'class':'company-directory-item'})
        l2 = [i.find('h6').text for i in skills_div]
