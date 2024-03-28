Platooning is a transportation technique that consists in grouping trucks or vehicles together to reduce CO2 emissions. A platoon consists of one or several vehicles, the first one in the platoon playing the role of the platoon leader, the other ones playing the role of followers.

1. A vehicle can  create a platoon: this vehicle is then the leader of this platoon. This vehicle informs neighbour cars about this platoon by sending a platoon information message (position, speed, acceleration) every second. Once followers have joined, it regularly informs ---every half second --- the followers of its current situation (speed, acceleration, direction, selected lane). Whenever there is an important modification of speed / acceleration / direction / lane, the leader immediately informs the followers. 
 
2. A follower can join a platoon only at the last position, i.e. behind all other vehicles of the platoon. When it joins the platoon, it informs the leader about this. When a follower wishes to leave the platoon, it informs all other vehicles of the platoon (with a "leave" message) and  then brakes or changes of lane.
  
3. Leaders and followers use front and back cameras to detect the lanes and the distance to other vehicles. The distance between vehicles within a platoon is considered to be between a min and a max distance. If there is less than the min distance between two vehicles, then the first vehicle detecting this situation broadcasts the information to all others and all vehicles of the platoon must perform an emergency braking. If the distance between two vehicles v1 and v2 ---with v1 before v2--- gets over max, then v2 and all the vehicles behind v2 have to leave the platoon. v2 is assumed to send the "leave" message. Obviously, one important goal of the platooning software is to keep the inter-vehicle distance between min and max so as to ensure that the platoon works for a long time. 

In a more advanced version of the platooning system, the platoon can split i.e. a given follower can decide to become the leader of all the followers behind it.

Use at least 2 blocks and at most 10 blocks.
