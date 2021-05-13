# Определить алгоритм с наилучшим сжатием

инфорамция по script в файле task1 

Результат:
список команд которыми получен результат с их выводами
вывод команды из которой видно какой из алгоритмов лучше

   12  zpool create poolmirror sdb sdc
   14  zfs create poolmirror/gzip
   16  zfs create poolmirror/gzip-n
   17  zfs create poolmirror/zle
   18  zfs create poolmirror/lsjb
   19  zfs create poolmirror/lz4
   26  zfs set compression=gzip poolmirror/gzip
   32  zfs set compression=lsjb poolmirror/lsjb
   33  zfs set compression=lzjb poolmirror/lsjb
   34  zfs set compression=lz4 poolmirror/lz4
   35  zfs list -o compression
   37  curl -o "War_and_Peace.txt" -J -L https://www.gutenberg.org/cache/epub/2600/pg2600.txt
   38  cd /poolmirror/gzip-n/
   39  curl -o "War_and_Peace.txt" -J -L https://www.gutenberg.org/cache/epub/2600/pg2600.txt
   40  cd /poolmirror/zle/
   41  curl -o "War_and_Peace.txt" -J -L https://www.gutenberg.org/cache/epub/2600/pg2600.tx
   42  cd /poolmirror/lsjb/
   43  curl -o "War_and_Peace.txt" -J -L https://www.gutenberg.org/cache/epub/2600/pg2600.t
   44  cd /poolmirror/lz4
   45  curl -o "War_and_Peace.txt" -J -L https://www.gutenberg.org/cache/epub/2600/pg2600.txt
   56  zfs get compressratio



NAME               PROPERTY       VALUE  SOURCE
poolmirror         compressratio  1.08x  -
poolmirror/gzip    compressratio  1.08x  -
poolmirror/gzip-n  compressratio  1.08x  -
poolmirror/lsjb    compressratio  1.07x  -
poolmirror/lz4     compressratio  1.08x  -
poolmirror/zle     compressratio  1.08x  -

# Определить настройки pool’a

инфорамция по script в файле task2

Результат:
список команд которыми восстановили pool . Желательно с  Output команд.
файл с описанием настроек settings

   79  curl -L "https://drive.google.com/uc?export=download&id=1KRBNW33QWqbvbVHa3hLJivOAt60yukkg" -o "zfs_task1.tar"
   82  tar -xvf zfs_task1.tar
   85  zpool import -d zpoolexport/
   87  zpool import -d zpoolexport/ otus
   88  zpool status

NAME  PROPERTY              VALUE                  SOURCE
otus  type                  filesystem             -
otus  creation              Fri May 15  4:00 2020  -
otus  used                  2.04M                  -
otus  available             350M                   -
otus  referenced            24K                    -
otus  compressratio         1.00x                  -
otus  mounted               yes                    -
otus  quota                 none                   default
otus  reservation           none                   default
otus  recordsize            128K                   local
otus  mountpoint            /otus                  default
otus  sharenfs              off                    default
otus  checksum              sha256                 local
otus  compression           zle                    local
otus  atime                 on                     default
otus  devices               on                     default
otus  exec                  on                     default
otus  setuid                on                     default
otus  readonly              off                    default
otus  zoned                 off                    default
otus  snapdir               hidden                 default
otus  aclinherit            restricted             default
otus  createtxg             1                      -
otus  canmount              on                     default
otus  xattr                 on                     default
otus  copies                1                      default
otus  version               5                      -
otus  utf8only              off                    -
otus  normalization         none                   -
otus  casesensitivity       sensitive              -
otus  vscan                 off                    default
otus  nbmand                off                    default
otus  sharesmb              off                    default
otus  refquota              none                   default
otus  refreservation        none                   default
otus  guid                  14592242904030363272   -
otus  primarycache          all                    default
otus  secondarycache        all                    default
otus  usedbysnapshots       0B                     -
otus  usedbydataset         24K                    -
otus  usedbychildren        2.01M                  -
otus  usedbyrefreservation  0B                     -
otus  logbias               latency                default
otus  objsetid              54                     -
otus  dedup                 off                    default
otus  mlslabel              none                   default
otus  sync                  standard               default
otus  dnodesize             legacy                 default
otus  refcompressratio      1.00x                  -
otus  written               24K                    -
otus  logicalused           1020K                  -
otus  logicalreferenced     12K                    -
otus  volmode               default                default
otus  filesystem_limit      none                   default
otus  snapshot_limit        none                   default
otus  filesystem_count      none                   default
otus  snapshot_count        none                   default
otus  snapdev               hidden                 default
otus  acltype               off                    default
otus  context               none                   default
otus  fscontext             none                   default
otus  defcontext            none                   default
otus  rootcontext           none                   default
otus  relatime              off                    default
otus  redundant_metadata    all                    default
otus  overlay               off                    default
otus  encryption            off                    default
otus  keylocation           none                   default
otus  keyformat             none                   default
otus  pbkdf2iters           0                      default
otus  special_small_blocks  0                      default

# Найти сообщение от преподавателей

инфорамция по script в файле task3

Результат:
список шагов которыми восстанавливали 
зашифрованное сообщение

   97  curl -L "https://drive.google.com/uc?export=download&id=1gH8gCL9y7Nd5Ti3IRmplZPF1XjzxeRAG" -o "otus_task2.file"
  104  zfs receive otus/storage@task2 < otus_task2.file
  113  find /otus/storage/ -name "secret_message"
  114  cat /otus/storage/task1/file_mess/secret_message

https://github.com/sindresorhus/awesome
