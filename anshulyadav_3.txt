import csv
from collections import OrderedDict, namedtuple

with open('C:\Users\AOC2\Desktop\shareData_inconsistant.csv') as f:
    reader = csv.reader(f)
    tup = namedtuple('tup', ['price', 'year', 'month'])
    d = OrderedDict()
    names = next(reader)[2:]
    for name in names:
        #initialize the dict
        d[name] = tup(0, 'year', 'month')
    for row in reader:
        year, month = row[:2]         # Use year, month, *prices = row in py3.x
        for name, price in zip(names, map(int, row[2:])): # map(int, prices) py3.x
            if d[name].price < price:
                d[name] = tup(price, year, month)
print d 
