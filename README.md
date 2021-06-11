# Programmable-Vehicles-Controll
Blueprint for Factorio AAI's Programmable Vehicles

Please read the AAI Programmable Vehicles tutorial beforehand:
https://forums.factorio.com/viewtopic.php?f=93&t=38475

ZONE CONTROLL:
1. Place one of the zone controll structures for iron ore, copper ore, uranium ore, coal, wood (trees) or stone.
2. Place the corresponding circle zone over a resource/ore patch with Zone Planner.
3. Use one of the Mining Controllers to send miners to the circle zone.
4. Once the ore will become smaller, zones with no ore anymore will be removed, so miners wont go there.

MINER CONTROLL:
1. Place one of the miner controlling structures.
2. Choose the number of miners you want to use.
3. Choose the miner type - it should be changed for Constant Combinator and the bottom left Arithmetic Combinator.

HAULER CONTROLL 2.0:
This massive controller can be used to automatically set multiple Haulers or Wardens to those vehicles, that need to have their ore picked up, have more ammo delivered or to be fixed. The controller checks for each Hauler where should he go. At first, it will check if the Hauler has all the items specified in the Constant Combinator #7. If not, it will go to the Depot specified in the Constant Combinator #7 and pick them up. If the Hauler is full, it will try to dump all the items to the Depots specified in Constant Combinators #8-13. Then it will look for any vehicle specified in Constant Combinator #2, that doesnt meet conditions from Constant Combinator #4 and #5. The closest target not meeting those conditions will have the priority to be serviced by Hauler or Warden. Once Haulers have nothing to do, they will park on Zones specified in Constant Combinator #6.

The blueprint has a default, most common setting. All settings can be done with Constant Combinators on the left side - you don't need to change anything else. The Controller can only controll one type of service vehicle (Hauler or Warden). The Controller can send Hauler/Waren to only one type of vehicle (Miner ID Signal or any military ID Signal) or to all the types of vehicles, using the Unit ID Signal (gray icon with "ID"). Make sure all the vehicles can accept items the Hauler wants to deliver to them. Also make sure the Miners can give the Hauler the ore it wants to pick up. You can do that by selecting the AI vehicle with Remote Controller and clicking on the Edit UnitData button.

Constant Combinator #1: Number of Haulers or Wardens to be used and the starting ID of them. Possible signals: AI Hauler ID Signal, AI Warden ID Signal, any positive N Signal
Constant Combinator #2: Number of Miners/Tanks to be serviced and the starting ID of them. Possible signals: any AI vehicle ID Signal or Unit ID Signal, any positive N Signal
Constant Combinator #3: Max service range - the maximum distance between the Hauler and the requesting vehicle, to allow for dispatch, Calculation speed - how fast the Controller will work - lower numbers will make it work faster. DO NOT SET BELOW 15! Possible signals: positive Distance Signal, 15+ Speed Signal
Constant Combinator #4: Maximum number of items for Miner to hold, after which the Hauler will be dispatched to it. Possible signals: any positive item Signal
Constant Combinator #5: Minimum number of items for Miner to have. If it has less, the Hauler will be sent. Possible signals: any positive item, Health, or Inventory Slot Signal
Constant Combinator #6: The starting id of a parking Zone - specify a zone where idle Haulers should park. Possible signals: any positive Zone Signal
Constant Combinator #7: Minimum number of items for Hauler to have and coordinates of the Supply Depo. Possible signals: any positive item Signal, X and Y Tile Position Signal
Constant Combinator #8-13: Cordinates of Depo, what can be delivered there. Possible signals: any positive item Signal, X and Y Tile Position Signal

DEFFENCE CONTROLLER:
Sends forces to the X Zones. If there's no X Zone, then each tank parks at the Parking Zone (the Zone Box Red).
Specify the starting ID of tank with AI vehicle ID Signal, number of tanks with N Signal and the type of Zone. If you want to change the type of tank, or typ of Zone, you need to change the signals in all Constant, Decider and Arithmetic Combinators.

DEPOTS:
If you want to set some different items to be accepted, click on the top right box of the Depot and change signals. Any positive Signall will make the Depot accept that item. The -1 Signal will make the Depo only give that item to the Hauler.

DEPLOYERS:
Coppy settings from the Constant Combinator to the Vehicle Deployer Deployed Unit Data using Shift+RMB and Shift+LMB before starting the Deployers!

MULTIDEPLOYER + DATA CONTROLL:
Multideployer are to be used with Data Controll Structures as an alternative to above Deployer Blueprints. The system scans area to check how many vehicles are there, before putting any new vehicle to the Deployer. To make it work you need to connect the Yellow Inserter next to the Deployer to the outputs of bottom-right Decider Combinator of Data Controll with a Green Wire, as shown in the picture.
