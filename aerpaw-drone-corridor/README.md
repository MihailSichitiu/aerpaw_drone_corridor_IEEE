## implementation

This is implementing using a block system.
The controlled airspace is defined using a center coordinate, and a size for each block.
Each block only allows one drone to occupy it, and drones must request permission to move into adjacent blocks.
The central controller ensures that every block adjacent to a drone is cleared out.
The central controller also provides functionality to generate a path plan for a drone using a basic pathfinder.

## running

```
docker-compose build

docker-compose up
```

You'll need to connect to each drone and set the following param:

```
mavproxy.py --master=tcp::14551

param set DISARM_DELAY 0
```

There's an open mavproxy port for each drone at `tcp:0.0.0.0:14551...n`.
This can be used for qgroundcontrol

Open `example-out.kml` in Google Earth to view the system as it's running.

`ground/server-testing/sendjson.sh` can be referred to as an example of how to interact with the server handling blocks and reservations.
The API is somewhat documented in `ground/server.py`.
You can also view the drone-server interactions in `drone/__init__.py`.
