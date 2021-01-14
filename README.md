# OverTheWire - Bandit

## SSH Information
#### Host: bandit.labs.overthewire.org
#### Port: 2220

## Level 0:
    ssh: 
        username@host -p[PortNumber]

## Level 1:
    Pretty straight forward

## Level 2:
    Use explicit filename for filenames with special characters
    eg: cat ./-

## Level 3:
    cat "file name"

## Level 4:
    Hidden file, use ls -a

## Level 5:
    Waste of time

## Level 6:
    Use find for proper filtering
    find ./ -type f -readable ! -executable -size 1033c

## Level 7:
    Use the find command again with a different set of filters

## Level 8:
    Use grep

## Level 9:
    Use uniq to find unique lines (make sure input is in sorted order first using sort)
    sort data.txt | uniq --unique

## Level 10:
    Use grep, treat binary file as text file using grep -a 'pattern'
    OR
    Use strings to find readable characters in a file as follows, then pass regular expression for the '=' pattern using grep -E
    strings fileName | grep -E "+="

## Level 11:
    Use base64 -d to decode the file

## Level 12:
    Decode it using ROT13

## Level 13:
    File appears to be a hex dump
    Use hexdump -C to show ASCII characters - looks like file has been compressed multiple times
    Do a reverse hexdump using xxd to get the binary file
    Use 'file' to understand theh filetype after each step
    Use a combination of gunzip/tar/bunzip to extract the filenames

## Level 14:
    Specify private key file using the -i param in ssh
    Use ssh bandit14@localhost -i private_key_file.sshkey

## Level 15:
    Use netcat to write the old password to port 30000
    echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000

## Level 16:
    Use openssl s_client to connect to localhost at port 30001
        openssl s_client -connect localhost:30001
    Submit current password to get the next one

## Level 17:
    Scan the range of ports using nmap:
        nmap -p 31000-32000 -sV
        sV is used for identifying services running on each port to find the SSL service
    Create the private_key_file.sshkey
    Update permissions for private_key_file.ssh using chmod
    Connect to bandit17 using ssh
    Use diff to compare the two files

## Level 18:
    ssh lets us execute commands while it's connecting
    Append cat readme to view the password before getting disconnected
        ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme




