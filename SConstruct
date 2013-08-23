import os

CacheDir(os.environ['HOME'] + '/.cache/scons')

Ntests = 100

# # just create a bunch of programs
# for i in range(Ntests):
#     os.system('cp hello.c hello-%04d.c' % i)

for i in range(Ntests):
    Program(target = 'hello-%04d-small' % i,
            source = 'hello-%04d.c' % i)
    Command(target = 'hello-%04d' % i,
            source = 'hello-%04d-small' % i,
            action = 'cp $SOURCE $TARGET && head -c 100000000 /dev/zero >> $TARGET')
for i in range(Ntests):
    NoCache(Command(target = 'greeting-%04d.txt' % i,
                    source = 'hello-%04d' % i,
                    action = './$SOURCE > $TARGET'))
