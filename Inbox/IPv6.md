

created: 2024-07-30 10:49

ipv6 uses 128bits as opposed to 32bits in ipv4
it is written in hexadecimal. because each decimal represent 4 bits we'l have 32 characters.
those characters are grouped into 8 groups.
group1:group2:...group8

![[Pasted image 20240730105336.png]]

the address is split into 2 groups
![[Pasted image 20240730105440.png]]


the upper 64 bits used for **routing** 
the lower 64 bits are for identifying the device.

the upper 64 bits are split into 2 blocks:
- upper 48 bits. used for **global network addresses** - routing over the internet.
- lower 16 bits are used for **subnet** by the network administrator
![[Pasted image 20240730105917.png]]

### Address Types and Scope

## References

1. 