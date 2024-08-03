
# Event-Driven Montage System 

### This is a lightweight component, it simplifies the Montage RPC process and use events to handle Montage's logic
#### In the example, includes `weapon switching` & `attack` & `combo` & `hitreact` & `weapon trails` & `weapon hit trace`


## Usage
#### Add component `CT_Cmpt_Montage` to any Actor, such as `BP_Weapon`, `BP_Character`, `BP_Ability`, etc.
![image](https://github.com/user-attachments/assets/8de464b4-dc00-4335-9650-b387a82d428f)


#### Regular Montage RPC
![image](https://github.com/user-attachments/assets/0216cbe1-cd42-4587-ad5e-2d0b50344be6)


#### RPC in MontageSystem
![image](https://github.com/user-attachments/assets/f23fab7a-1661-423c-a272-e140691cb03c)



# Network Options
![image](https://github.com/user-attachments/assets/eb6f5250-987c-4fd0-a8b2-bd17ab731a75)

## NetworkPriority
#### `Server`: Montage will be played on the server first and then multicast to all clients
#### `OwningClient`: montage will be played on the OwningClient first, then played on Server, and finally Multicast to other Clients

## NetworkDelayOffset 
#### If True, When network is bad, Other clients will skip the delayed time
#### For example, you played a 1-second Montage (`NetworkPriority=OwningClient`), and another client network delay is 0.5-second. this client will saw your montage is played starting from 0.5. This will ensure that other clients are at the same progress as your montage



# Handle `Notify` in `Actor`
#### I prefer to handle Notify in Actor instead of creating `BP_Notify` files because in `Actor` can easily modify values ​​and change resource files at runtime.
#### In the example. I created a BP_Weapon that handles `Combo` & `Weapon Trails` & `HitTrace` notifies, and then used `Child Class` to change Trails FX. I think this way is more flexible and clean. This is just optional, you can also use BP_Notify if you want

#### using the built-in `MontageNotify` and `MontageNotifyWindow`.
![image](https://github.com/user-attachments/assets/932d2a28-c733-4560-a1dd-bdb89f0a2a31)

#### Then handle Notifys through the component's Events. This way, all the logic of the Montage can be kept in one BP_Actor
![image](https://github.com/user-attachments/assets/ac4bc0f3-868f-4cd5-aff4-c0c4f77278ce)

#### There is a useful function `NotifyStartsWith?` in the component. It's used to split NotifyName and allowing you to simply handle complex Notify
![image](https://github.com/user-attachments/assets/fa6a5d72-6443-4911-b1b7-b61bdfd912b8)



# Other Events
![image](https://github.com/user-attachments/assets/fa7e3e11-88be-4d88-bd8e-f4013280c398)

#### In short, they are events within PlayMontage.
![image](https://github.com/user-attachments/assets/8ffc1305-f9ae-40ae-9233-bb0786de5a22)


