# python
something interesting
learn_backup.py
#Filename:learn_backup.py

import os
import time

source = r'D:\test-backup\515.pdf'          
target_dir = r'D:\backup\\'
today = target_dir + time.strftime('%Y%m%d')
now = time.strftime('%H%M%S')

comment = raw_input('Enter a comment:')
if len(comment) == 0:
    target = today + os.sep + now + '.rar'
else:
    target = today + os.sep + now + '_' + \
             comment + '.rar'

if not os.path.exists(today):
    os.mkdir(today)
    print 'Successfully created directory',today

rar_command = "winrar a -r %s %s"%(target,''.join(source))

if os.system(rar_command) == 0:
    print 'Successful backup to',target
else:
    print 'Backup Failed'
