title: "Read file and get internet data"
date: 2015-04-18 18:41:17
tags: [python,web api,]
categories: [python,junior]
---

in short
```
import csv
with open(myfilepath, 'rb') as f: ## must read binary
    mycsv = csv.reader(f)
    for row in mycsv:
        text = row[1]
```

example
```
import urllib2
import pprint
import json
import csv
import time 
with open('fileWriter.csv', 'wb') as csvfile2:
        spamwriter = csv.writer(csvfile2, delimiter=' ',
                            quotechar=' ', quoting=csv.QUOTE_MINIMAL)
        with open('fileReader.csv', 'rb') as csvfile:
                spamreader = csv.reader(csvfile, delimiter=' ', quotechar=',')
                for row in spamreader:
                    time.sleep(2)
                    info =''.join(row).split(',')
                    address = info[1] ##get address
                    geocode_url = "http://maps.googleapis.com/maps/api/geocode/json?address=%s" % urllib2.quote(address)
                    req = urllib2.urlopen(geocode_url)
                    jsonResponse = json.loads(req.read())
                    pprint.pprint(jsonResponse)
                    geometry=None
                    try:
                        geometry=jsonResponse['results'][0]['geometry']['bounds']['southwest']
                    except Exception, e:
                        geometry=jsonResponse['results'][0]['geometry']['location']
                    finally:
                        pass
                    spamwriter.writerow([info[0]]+[info[1]]+[geometry['lat']]+[geometry['lng']])
```