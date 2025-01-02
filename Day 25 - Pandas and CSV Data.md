# Pandas and CSV Data


* Pandas - Data Analysis library
* CSV Python Module

## Pandas
Pandas library has two different types of data. Dataframe and series. The whole data is considered to be the dataframe, can be viewed as a 2 Dimensional Matrix. The series is considered to be 1D.

Series = Column

Dataframe = Multiple columns

```python
#with open('weather_data.csv') as weather_data:
#   data = weather_data.readlines()
#    print(data)

import csv
import pandas

#with open('weather_data.csv') as data_file:
#    data = csv.reader(data_file)
#    temperatures = []
#    for row in data:
#        if row[1] != 'temp':
#            temperature = int(row[1])
#            temperatures.append(temperature)
#    print(temperatures)

data = pandas.read_csv('weather_data.csv')
#print(type(data))
#print(type(data['day']))

data_dict = data.to_dict()
#print(data_dict['condition'])

temp_list = data['temp'].to_list()
#print(temp_list)
# classic way
average = sum(temp_list) / len(temp_list)
#print(average)

# calculate average using pandas
#print(data['temp'].mean())

# calculate maximum temperature using pandas
#print(data['temp'].max())

# calculate minimum temperature using pandas
#print(data['temp'].min())

# ver los datos del Lunes
#print(data[data['day'] == 'Monday'])

# calculate row of data with the maximum temperature
day_with_maximum_temp = data[data['temp'] == data['temp'].max()]
#print(day_with_maximum_temp)

# DataFrame[Display row that fufills the condition inside this]
monday = data[data['day'] == 'Monday']
print((monday['temp'] * 9 / 5) + 32 )
```

