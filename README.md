# openstack

## Install ksmtuned
`dnf install ksmtuned`

Update the config
`vi /etc/ksmtuned`

Track the results of ksmd on memory dedupe - display ksm stats every 15s for 60m
``` bash

./ksmstat.sh 240 15

----------------------------------------------------------------------------
http://www.kernel.org/doc/Documentation/vm/ksm.txt :

The effectiveness of KSM and MADV_MERGEABLE is shown in /sys/kernel/mm/ksm/:

pages_shared     - how many shared pages are being used
pages_sharing    - how many more sites are sharing them i.e. how much saved
pages_unshared   - how many pages unique but repeatedly checked for merging
pages_volatile   - how many pages changing too fast to be placed in a tree
full_scans       - how many times all mergeable areas have been scanned

A high ratio of pages_sharing to pages_shared indicates good sharing, but
a high ratio of pages_unshared to pages_sharing indicates wasted effort.
pages_volatile embraces several different kinds of activity, but a high
proportion there would also indicate poor use of madvise MADV_MERGEABLE.
----------------------------------------------------------------------------

         Shared        Sharing       Unshared       Volatile      Sharing:Shared     Unshare:Sharing           Saved
         567947        2161822        2656261        6218126              3.80:1              1.22:1           8444M

```
