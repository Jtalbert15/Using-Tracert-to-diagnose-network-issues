# Using-Tracert-to-diagnose-network-issues
Using Tracert to diagnose network issues

To start, boot up your Windows server 2019 VM

<img width="1018" alt="Screenshot 2024-06-05 at 10 08 44 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/6e6aadfd-ced9-4f65-afdc-6c3a5808f0fc">

Now in the bottom left click on the search icon and type cmd

<img width="1018" alt="Screenshot 2024-06-05 at 10 09 35 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/06a1a85d-9b31-4ce5-8084-38a1697b897a">

Click on command prompt and a terminal will pop up

<img width="1027" alt="Screenshot 2024-06-05 at 10 10 32 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/f6d1d77d-6423-4954-a17e-c9802e73a363">

To start lets see if we can ping an Ip address outside of our network

We can do this by using the ping command followed by the site we'd like a response from

For us let's try microsoft.com

<img width="1020" alt="Screenshot 2024-06-05 at 10 15 03 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/47179fed-daf3-4097-8afa-061d012e92ea">

We can see we sent 4 packets and all 4 were received with none lost

We can also see how much data was sent (32 bytes each) the time it took (in milliseconds) and the TTL (Time to Live)

Time to live is a feature that stops our data from endlessly floating around on the internet

Each time our request is received by a network the TTL is reduced by 1

Along with that information we can see the IP address we pinged from microsoft

The IP address we pinged was 20.231.239.246 which is a class A network

Microsoft owns every IP address that begins with 20.

Now let's use tracert. Tracert is a feature that modifies the TTL so that we can locate where along in the transmission of the data our error occurred 

Before doing so let's clear our terminal. We can do this by typing cls followed by hitting enter

<img width="977" alt="Screenshot 2024-06-05 at 10 24 59 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/a340550f-9674-422b-bf53-66fd41b772bb">

Now instead of typing ping microsoft.com we are going to type tracert microsoft.com

<img width="965" alt="Screenshot 2024-06-05 at 10 26 18 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/9f5ece95-4e1b-4e2f-ae07-34c20ac920e9">

This may take a while as it will start with a TTL of 1 and end up going all the way to 30

<img width="979" alt="Screenshot 2024-06-05 at 10 29 14 AM" src="https://github.com/Jtalbert15/Using-Tracert-to-diagnose-network-issues/assets/66844406/c8317514-5a33-4eb5-9b70-3606ba2613cd">

Now we can see for the most part the path our packets went along it's way to its final destination

Note some of our requests did time out but that's not due to failure. That ip address just may not support what tracert does

We can see on step 20 we have reached the same IP address that we pinged using the ping command
