1. Ouvrir le fichier pcap avec Wireshark
2. En regardant les statistiques ont remarque quelques communications HTTP
3. Je commence par suivre les flow, pour ça je clique sur le premier paquet et sélectionne "follow - TCP Stream", ensuite je suis les streams un a un, le stream 1 nous montre beaucoup de GET vers des URL bizarre mais en faite ça sert à rien :D
4. Le stream 2 nous aprend que l'attaquant est root sur la machine et qu'il a extrait des fichiers vers pastebin
5. Le flag doit être dans les données extraitent, mais les communications sont chiffré donc il faut commencer par déchiffrer, pour ça on va dans "edit - preferences - TLS" et on charge le fichier **secrets.log** en tant que "(Pre)-Master-Secret log filename"
6. Ensuite on peut filtrer dans wireshark sur le nom DNS pastebin pour obtenir les paquets en direction de pastebin, filtre : http.host == "pastebin.com"
7. Enfin, suivre les stream HTTP pour obtenir le flag au millieu de numéro de carte bancaire :)
