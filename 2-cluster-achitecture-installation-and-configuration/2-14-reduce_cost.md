During this course, we will be creating nodes (VMs) on Google Cloud. There are many advantages to using Cloud VMs compared to creating VMs on your laptop using some hypervisors. Especially time, flexibility, resource consumption to name few.

At the same time, It is very important to keep the costs down when using any cloud provider. Here are the three steps I use.

    Free Tier: Take Advantage of Free Tier. Cloud Providers such as Google Cloud, Azure, and AWS offer a free tier (about $300). This itself is more than enough to complete this course (if you follow below TIP#3).

    Cleanup Unused Resources: Delete the resources (if not needed for next practice session). In any practice session (which could be ~2hrs to ~5hrs), we create different types of resources, including Pods, Deployments, PVs...these resources might not be useful for next sessions. It is important to cleanup(delete) the resources before you close the practice session. By doing this we can save resource consumption costs such as Storage, Bandwidth.

    Schedule "Shutdown" cronjob: One important way to save cloud costs is by shutting down the VMs when they are not in use. Typically, we tend to forget this at the end of the practice session. To avoid this and save costs, I have made the below "crontab" entry into the /etc/crontab file on all nodes inside the K8s cluster (including Master and Worker nodes). This cronjob will run the respective shutdown command every five hours, in case if the node is up and running during that time, it will shut down the node. This itself will save about 95% of the cloud costs. This might not be the most sophisticated solution, but this works. 

      #run this command on your command prompt. It will create a new entry at the end of /etc/crontab file.

      echo "0 */5 * * * root /sbin/shutdown -h now" >> /etc/crontab

I hope this helps!

Thanks

Your Instructor

Srinath Challa 
