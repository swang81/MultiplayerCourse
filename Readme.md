# Creation and Destruction

- When a replicated actor is spawned on the server, it will generate remote proxies of itself on all connected clients. The key point is that you need to do this from the server.

-  

   

# Movement replication
- if an authoritative actor has replicated movement enabled, or bReplicatedMovement is set to true in C++, it will automatically replicate its Location, Rotation and Velocity. 


# Variable Replication
- Any variables (replicated) will automatically replicate from the authoritative actor to its remote proxies whenever their values change. 

# Remote Procedure Calls (RPCs)
- No matter what machine an RPC is initially called on, its implementation will run only on the machine it is intended for. 
- It has 3 types of RPCs;
	- Server(only runs on the server)
	- Client(only runs on the actor's owning client)
	- NetMulticast(runs on every machine connected to the session, including the server )
	

# NetworkRole & Authority

- An actor network role determines whose machine has control over the actor during a network game. 
- Authoritative actor control over that actor's state. It will replicate information to other machines within the network multiplayer session. 
- Server always has authority over the game state and information will always replicate from the server to clients. 
- Remote proxy is a copy of that Actor on a remote machine, and it receives replicated information from the authoritative actor. 
- We can get local role of an actor by calling the `AActor::GetLocalRole` function. The return type can take the following values:
  - ROLE_None
  - ROLE_Authority (On the server, or on the client without replicated)
  - ROLE_SimulatedProxy (On the client)
  - ROLE_AutonomousProxy(On the client  controlled by the player )
- We can check `GetLocalRole() == ROLE_Authority` to see if the local machine has authority over the actor. `AActor::HasAuthority` is a shorthand way of doing this check. 

# Variable Replication

​			
