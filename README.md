# docker-compose-typo3
For version use composer
- docker-compose up -d
- docker exec -it typo3_v12_php bash
- composer create-project "typo3/cms-base-distribution:^12.4" .
- go localhost:81/typo3/install.php and follow step to install Typo3

For version use symlink (old version)
docker-compose -f docker-compose-symlink.yml up -d
