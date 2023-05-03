1. On a des evtx, reflexe : utiliser chainsaw !
2. On lance la commande suivante : ./chainsaw_x86_64-unknown-linux-gnu hunt -r rules/ ../Logs -s sigma/rules --mapping mappings/sigma-event-logs-all.yml --level critical
3. On remarque qu'un script a été téléchargé sur github, on remarque également que ce script sert à lancer mimikatz
4. Si on regarde la totalité des logs (on retire le --level critical) on a beaucoup trop d'événement
5. Je tente le "low hanging fruit" : ./chainsaw_x86_64-unknown-linux-gnu hunt -r rules/ ../Logs -s sigma/rules --mapping mappings/sigma-event-logs-all.yml | grep 'HTB'
Boom ! Le flag !
