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
  7. Optional: iobroker_E3DC Menue and loading scripts by ArnoD15 https://github.com/ArnoD15/iobroker_E3DC
  9. Optional: PV-Prognose
  

Order for setup:
1. Install all modules mentioned above + Grafana and do the basic config. iobroker_E3DC is optional at this point.

2. Import the 0_userdata.0.E3DC_Grid_Load.json properties to you Object folder in order to create the variables needed later (https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/0_userdata.0.E3DC_Grid_Load.json)
   ![grafik](https://github.com/user-attachments/assets/125fdfb8-2403-4675-9dae-1e0d7d3f4a6b)

4. In order to get the energy costs loaded every day around 15 CET add the following script to Scripts as JS-script: https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/Tibber_load_PricesTomorrow_to_Influx.txt
   You have to replace the "tibberlink.0.Homes.*****" with your Home ID! of cause you can also use any other service providing the data to you!
   ![grafik](https://github.com/user-attachments/assets/e4f3e580-f0ac-413a-a320-65e2af534bcb)

5. In order to copy settings at 00:00 CET to the new day you need to import the JS-script: https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/E3DC_Grid_Load_Midnight_Copy_job
   ![grafik](https://github.com/user-attachments/assets/1ac713cb-effc-4a0c-8db2-9f5ba9cad1e5)

6. With the two scripts Tibber.E2DC_Grid_Load_Execution and Tibber.E3DC_Grid_Load_set_current_load "E3/DC RSCP" will control you E3DC based on the values selected in 0_userdata.0.E3DC_Grid_Load
   load both scripts:
        a: https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/common.Tibber.E2DC_Grid_Load_Execution.xml
          ![grafik](https://github.com/user-attachments/assets/a95e57f3-c95f-41a7-b0cf-63d70ef10d3b)
        b: https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/common.Tibber.E3DC_Grid_Load_set_current_load.xml
          ![grafik](https://github.com/user-attachments/assets/fc272d47-adfc-4a17-85e2-dda52cf88c5f)

7. In Grafana import the config: https://github.com/ESDN83/E3DC_IObroker_Speicher_Laden/blob/main/Grafana_Tibber_View.json
   Once the data is loaded, the Dashboard should look like this: 
   ![grafik](https://github.com/user-attachments/assets/3722e9fc-6364-4636-bd34-ba29316063f1)

8. Optional:
   a: I use Charge_Control by ArnoD15 and use the estimated energy produced next day on my VIS. if you like to use it you need to follow the instructions on https://github.com/ArnoD15/iobroker_E3DC
   b: I use PV-Prognose to get another forecast value visualized too + I can use the forecast date in my other Grafana Dashboards.
     
8. finally load the VIS View using the file:
   But you need to update the URL for Grafana used...Extracktz it following the below image from Grafana and remove the time frame defined for the Today and tomorrow view update the URL's:
   ![grafik](https://github.com/user-attachments/assets/67cc3282-977e-41ad-88f5-b143adc6ca15)

