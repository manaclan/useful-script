# mkdir and do rsync from csv file
```sh
f = open('id.csv', 'r')
lines = f.readlines()
all_ids = []
for line in lines:
  splits = line.replace('\n','').split(',')
  all_ids.append([splits[0],splits[1]])

f = open('run.sh','w')
for i in all_ids:
  f.write( 'mkdir {} && rsync -avz --include="{}_180*" --include="{}_265*"	--include="{}_180*" --include="{}_265*" --exclude="*" 192.168.1.33:/home/vinhngo/data_41/ ./{} && ls '.format(i[0],i[0],i[0],i[1],i[1],i[0])
  +'\n')
```
