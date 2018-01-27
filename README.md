# python_learning
record the learning progress of python in dataquest

import csv
file1 = open('guns.csv','r')
file2 = csv.reader(file1)
data = list(file2)
print(data[0:5])


headers = data[0]
data = data[1:]
print(headers)
print(data[0:5])

years = [i[1] for i in data]
year_counts ={}
for i in years:
    if i in year_counts:
        year_counts[i] += 1
    else:
        year_counts[i] = 1
print(year_counts)

import datetime
import csv
file1 = open('guns.csv','r')
file2 = csv.reader(file1)
data = list(file2)
data = data[1:]
dates =[]
for i in data:
    a = datetime.datetime(year=int(i[1]),month=int(i[2]), day=1)
    dates.append(a)
print(dates[0:5])

date_counts={}
for i in dates:
    if i in date_counts:
        date_counts[i] +=1
    else:
        date_counts[i] = 1
print(date_counts)

import datetime
import csv
file1 = open('guns.csv','r')
file2 = csv.reader(file1)
data = list(file2)
data = data[1:]
sex = [i[5] for i in data]
sex_counts={}
for i in sex:
    if i in sex_counts:
        sex_counts[i] += 11
    else:
        sex_counts[i] = 1
race = [i[7] for i in data]
race_counts={}
for i in race:
    if i in race_counts:
        race_counts[i] += 1
    else:
        race_counts[i] = 1
print(sex_counts)
print(race_counts)

import re
import csv
file = open('census.csv','r')
census=list(csv.reader(file))
file1 = open('guns.csv','r')
file2 = csv.reader(file1)
data = list(file2)
data=data[1:]
race = [i[7] for i in data]
mapping ={}
set_race =set(race)
#print(set_race)
#print(census)
mapping={"Asian/Pacific Islande":int(census[1][14])+int(census[1][15]),"Black"
         :int(census[1][12]),"Native American/Native Alaskan":int(census[1][13])
         ,"Hispanic":int(census[1][11]),"White":int(census[1][10])}

race_per_hundredk ={}
race_counts={}
for i in race:
    if i in race_counts:
        race_counts[i] += 1
    else:
        race_counts[i] = 1
for i in race_counts:
    for j in mapping:
        if i==j:
            race_per_hundredk[i]=(int(race_counts[i])/mapping[j])*100000
print(race_per_hundredk)


intents = [i[3] for i in data]
races = [i[7] for i in data]
homicide_race_counts ={}
for i , j in enumerate(races):
    if intents[i] =='Homicide':
        if j in homicide_race_counts:
            homicide_race_counts[j] += 1
        else:
            homicide_race_counts[j] = 1
homicide_race_per_hundredk ={}
for i in homicide_race_counts:
    for j in mapping:
        if i==j:
            homicide_race_per_hundredk[i]=(int(homicide_race_counts[i])/mapping[j])*100000
print(homicide_race_per_hundredk)
