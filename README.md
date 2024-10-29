# E3DC_IObroker_Speicher_Laden
IObroker Solution for loading E3DC Solar System Battery

This solution is a collection of scripts intend to offer a Menu for Loading your E3DC Batter based on dynamic energy costs:

![grafik](https://github.com/user-attachments/assets/1b74083c-886f-4108-801e-de24f2d76415)


What did I use:

  1. IObroker
  2. Grafana
  3. tibberlink Adapter in IOBroker
  4. E3/DC RSCP Adapter in IOBroker
  5. javascript Adapter in IOBroker
  6. influxdb + influxdb Adapter in IOBroker
  7. iobroker_E3DC Menue and loading scripts by ArnoD15 https://github.com/ArnoD15/iobroker_E3DC
  

Order for setup:
Install all modules mentiond above + Ggrafana and do the basic confg.
iobroker_E3DC is optional at this point.

In order to get the costs loaded add the following script to 
