# python_script_convert_to_AWS_JSON
Python script - conversion json for file to AWS compliance JSON standard

# Project goal:

Automatic conversion files imported from other supplier and convert it into AWS Route R53 JSON standard:

# Python script:

```
import json
import sys
import os

# Folder with old json domain's files (before convertion)
file_list = os.listdir("/Users/andrzejhochbaum/json/zones")
for zone_name in file_list:
    # Create file compliance with AWS json format
    with open('/Users/andrzejhochbaum/json/zones/%s' %zone_name, 'r') as zone:
      obj = json.load(zone)
    # write ouput to the file:
    file = open('/Users/andrzejhochbaum/json/export_aws/%s' %zone_name,  'a')
    sys.stdout = file

    # First fix block of file 
    print "{"
    print " "*2,'"Comment": "A new record set for the zone.",'
    print " "*2,'"Changes": ['

    # For each DNS records like A, CNAME and TXT perform convertion
    records = ["a", "cname", "txt"]
    for pp in records: 
      if ("%s" %(pp)) in obj:
          i = 0 
          while i < len(obj["%s" %(pp)]):
            print " "*4,'{'
            print " "*6,'"Action": "CREATE",'
            print " "*6,'"ResourceRecordSet": {'
            if (obj["%s" %(pp)][i]['name'] == ""):
              print " "*8,'"Name": ' + '"' + obj["%s" %(pp)][i]['name'] +  '%s' %zone_name  + '"' +' ,'
            else:
              print " "*8,'"Name": ' + '"' + obj["%s" %(pp)][i]['name'] +  '.%s' %zone_name  + '"' +' ,'
            tp = pp.upper()
            print " "*8,'"Type": "%s" ,' %(tp)
            print " "*8,'"TTL": ',obj["%s" %(pp)][i]['ttl'],","
            print " "*8,'"ResourceRecords": ['
            print " "*10,'{'
            if pp == 'txt':
              print " "*12,'"Value": ' + '"\\"' + obj["%s" %(pp)][i]['target'] + '\\""'
            else:
              print " "*12,'"Value": ' + '"' + obj["%s" %(pp)][i]['target'] + '"'
            print " "*10,'}'
            print " "*8,']'
            print " "*6,'}'
            print " "*4,'},'
            i += 1
      else:
          print "No data"

    # Loop for Record MX
    records = ["mx"]
    for pp in records: 
      if ("%s" %(pp)) in obj:
          i = 0 
          while i < len(obj["%s" %(pp)]):
            countr = len(obj["%s" %(pp)])
            lnr = countr - 1
            if i == 0:
                print " "*4,'{'
                print " "*6,'"Action": "CREATE",'
                print " "*6,'"ResourceRecordSet": {'
                if (obj["%s" %(pp)][i]['name'] == ""):
                  print " "*8,'"Name": ' + '"' + obj["%s" %(pp)][i]['name'] +  '%s' %zone_name  + '"' +' ,'
                else:
                  print " "*8,'"Name": ' + '"' + obj["%s" %(pp)][i]['name'] +  '.%s' %zone_name  + '"' +' ,'
                tp = pp.upper()
                print " "*8,'"Type": "%s" ,' %(tp)
                print " "*8,'"TTL": ',obj["%s" %(pp)][i]['ttl'],","
                print " "*8,'"ResourceRecords": ['
                if countr == 1:
                    print " "*10,'{'
                    print " "*12,'"Value": ','"',obj["%s" %(pp)][i]['priority'],obj["%s" %(pp)][i]['target'],'"'
                    print " "*10,'}'
                else:
                    print " "*10,'{'
                    print " "*12,'"Value": ','"',obj["%s" %(pp)][i]['priority'],obj["%s" %(pp)][i]['target'],'"'
                    print " "*10,'},'

            elif i < lnr and i != 0:
                print " "*10,'{'
                print " "*12,'"Value": ','"',obj["%s" %(pp)][i]['priority'],obj["%s" %(pp)][i]['target'],'"'
                print " "*10,'},'
            else:
                print " "*10,'{'
                print " "*12,'"Value": ','"',obj["%s" %(pp)][i]['priority'],obj["%s" %(pp)][i]['target'],'"'
                print " "*10,'}'

            
            i += 1
      else:
          print "No data"
    
    
    # CLose block of file
    print " "*8,']'
    print " "*6,'}'
    print " "*4,'}'
  
    print " "*2,']'
    print "}"

    file.close()
```
