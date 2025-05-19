## File Transfer Application: DRTP over UDP (application.py)

Ensure Python is installed on your system.

Open Terminal in Ubuntu VM:

From UbuntuVM terminal, install mininet:

`sudo apt-get update` 

`sudo apt-get install mininet`

`sudo mn -c` - clear existing action in mininet if needed


Install Xterm in Mininet:

`sudo apt-get install xterm`

Run the Topology File to enter Mininet

`sudo python3 simple-topo.py` - This configures the virtual network environment within Mininet.

Useful Mininet Commands:

`net` Shows the network topology, listing all hosts, switches, and connections.

`nodes` Lists all nodes, including hosts and switches, in the network.



## Running the DRTP Application:

Start the DRTP application in server mode before launching the client. Typically, the server runs on xterm h2 and the client on xterm h1.


### How to Run the Server:

-s, --server Run in server mode
`python3 application.py -s`

-sp, --save_path: path for files. default: files_downloaded
`python3 application.py -s -sp files_downloaded`


### How to Run the Client:

-c, --client Run in client mode
`python3 application.py -c`

-f, --file Name of the file to send
`python3 application.py -c -f picture.jpg`


#### Server & Client Options:

-h, --help for info on how to use the argparse flags
`python3 application.py -s -h`

-i, --ip IP address default 127.0.0.1, same on server mode and client mode.
`python3 application.py -s -i 127.0.0.1`

-p, --port Port, default 8088, same on server mode and client mode.
`python3 application.py -s -p 8080`

-r, --reliability gbn, same on server mode and client mode.
`python3 application.py -s -r gbn`
`python3 application.py -c -r gbn`

-w, --window Set the window size, default 3 packets, must be same on server mode and client mode.
`python3 application.py -s -w 3`
`python3 application.py -c -w 3`


#### Examples:

# Example running the server

python3 application.py -s -sp files_downloaded -i 127.0.0.1 -p 8088 -r gbn -w 3

# Example running the client

python3 application.py -c -f iceland.jpg -i 127.0.0.1 -p 8088 -r gbn -w 3
