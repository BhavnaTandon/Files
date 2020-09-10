#  Write a program to read through the mbox-short.txt and figure out the distribution by hour of the day for each of the messages. You can pull the hour out from the 'From ' line by finding the time and then splitting the string a second time using a colon. From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008. Once you have accumulated the counts for each hour, print out the counts, sorted by hour as shown below
name = input("Enter file:")
if len(name) < 1 : name = "mbox-short.txt"
handle = open(name)
time = list()
hours = list()
final = list()
counts = dict()
for line in handle:
    words = line.split()
    if len(words) < 1:
        continue
    if words[0] != 'From':
        continue
    time.append(words[5])
#print(time)
for t in time:
    h = t.split(':')
    hours.append(h[0])
#print(hours)
for hour in hours:
    counts[hour] = counts.get(hour,0) + 1
#print(counts)
final = sorted([k,v] for k,v in counts.items())
for k,v in final:
    print(k,v)
