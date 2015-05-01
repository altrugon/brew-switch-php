#Variables
cellar_path='/usr/local/Cellar/'
pwd=`pwd`

echo "== PHP in use =="
php -v
cd $cellar_path
echo -e "\n== PHP versions at: $cellar_path =="
ls -d php??/ | sed 's#/##'| awk '{print}' ORS='  '
echo -e "\n----------------------------------------------------"

echo -n "Which PHP would you like to use? (0 cancel): php"
read php_xx
if [ $php_xx -ne 0 ] ; then
  phpxx=php$php_xx
  cd $phpxx
  echo ""
  echo "== Available $phpxx versions =="
  ls -d */ | sed 's#/##'| awk '{print}' ORS='  '
  echo -e "\n----------------------------------------------------"
  echo -n "Which version? (0 cancel): "
  read php_v

  if [ $php_v != '0' ] ; then
    #echo -en "\nAre you sure you want to switch to PHP $php_v? (y/n): "
    echo -en "\nRun \`brew switch $phpxx $php_v\` ? (y/n): "
    read brew_switch

    if [ $brew_switch  = 'y' ] ; then
      brew switch $phpxx $php_v
      echo -en "\nRun \`brew link --overwrite $phpxx\` ? (y/n): "
      read brew_link

      if [ $brew_link  = 'y' ] ; then
        brew link --overwrite $phpxx
      fi

      echo -e "\n== Remember to edit your httpd.conf and then restart Apache. =="
    fi
  fi
fi

cd $pwd #Is this needed?