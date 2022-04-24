# FT-Manager-0.1x
A External HD Manager for Mac OS X
#!/bin/bash

echo "Enter the name of the external hard drive:"
read name

echo "Enter the path of the external hard drive:"
read path

echo "Adding $name to fstab"
## if the name is not verified 404 error will be thrown

echo "# $name" >> /etc/fstab
echo "$path /media/$name auto noauto,user 0 0" >> /etc/fstab

## automaticly detect the conneceted external harddrives
read -p "Do you want to add the external harddrives automatically? (y/n)" -n 1 -r
echo    # (optional) move to a new line
if [[ $REPLY =~ ^[Yy]$ ]]
then
    echo "Adding external harddrives automatically"
    mount -a
else
    echo "Adding external harddrives manually"
    echo "Mounting external harddrives"
    mount -a
fi 
echo "Done"
pause
