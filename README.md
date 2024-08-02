
# Event-Driven Montage System 

### This is a very lightweight system designed to simplify Montage RPC and avoid using `BP_Notify`. 
#### In the example, includes `weapon switching` & `attack` & `combo` & `hitreact` & `weapon trials` & `weapon trace`
#### Add component `CT_Cmpt_Montage` to any Actor, such as `BP_Weapon`, `BP_Character`, `BP_Ability`, etc.
![image](https://github.com/user-attachments/assets/8de464b4-dc00-4335-9650-b387a82d428f)



#### Regular Montage RPC
![image](https://github.com/user-attachments/assets/0216cbe1-cd42-4587-ad5e-2d0b50344be6)


#### RPC in MontageSystem
![image](https://github.com/user-attachments/assets/f23fab7a-1661-423c-a272-e140691cb03c)



# Why Avoid Using `BP_Notify`?
#### Usually, you might create a large number of `Notify` or `NotifyState` to handle  Montage events. Many of these Notify might only be used once or just call other functions via `Cast to XXXCharacter` and `GetComponentByClass`. This can lead to an excessive number of Notify files, making the project difficult to maintain.
#### Additionally, changing values or resource files at runtime in `BP_Notify` is not easy.
![image](https://github.com/user-attachments/assets/71d3a403-e4cd-40b3-86f6-5ec692fbde79)


#### In this component, I recommend using the built-in `MontageNotify` and `MontageNotifyWindow`.
![image](https://github.com/user-attachments/assets/932d2a28-c733-4560-a1dd-bdb89f0a2a31)

#### Then handle Notifys through the component's Events. This way, all the logic of the Montage can be kept in one BP_Actor, and you can easily modify the values and resource files at runtime.
![image](https://github.com/user-attachments/assets/ac4bc0f3-868f-4cd5-aff4-c0c4f77278ce)




# Other Events
![image](https://github.com/user-attachments/assets/fa7e3e11-88be-4d88-bd8e-f4013280c398)

#### In short, they are events within PlayMontage.
![image](https://github.com/user-attachments/assets/8ffc1305-f9ae-40ae-9233-bb0786de5a22)



# Network Options
![image](https://github.com/user-attachments/assets/eb6f5250-987c-4fd0-a8b2-bd17ab731a75)

## NetworkPriority
#### Server: Montage will be played on the server first and then multicast to all clients
#### OwningClient: montage will be played on the OwningClient first, then played on Server, and finally Multicast to other Clients

## NetworkDelayOffset 
#### If True, When network is bad, the montage will not play completely.
#### For example, you played a 1-second Montage, and another client network delay is 0.5-seconds. this client saw montage played starting from 0.5
