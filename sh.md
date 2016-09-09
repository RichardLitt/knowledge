# sh

### Killing background processes

    ps -eaf | grep <process>

Example:

    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 31798     1   0  5:10PM ??         0:00.36 ipfs daemon
      501 32228 31854   0  5:10PM ttys000    0:00.00 grep ipfs
    The-Atrium-of-Time:~ richard$ kill 31798
    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 32248 31854   0  5:10PM ttys000    0:00.00 grep ipfs
