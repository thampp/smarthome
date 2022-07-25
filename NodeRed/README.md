# Node Red Flows

## ViessmannHeizungsFlow
Uses the Viessman REST APIs to fetch heating information and publish it to InfluxDB.
The specific example is configures for a Vitoligno Pellets heating but it should be possible to adjust to other heatings.

For starters you will have to enter intial token and id values in the node **Set initial access token and IDs** After that token refresh should work automatically.
You may then want to have a look at the node **Extract Values** You will find a configuration "table" on top that defines which 
of the many metrics the Viessmann API can return are retrieved, what their name, id and unit is.
You can adjust that to your heating by adding/removing the ones that the API supports for your heating.

You will also find the workaround for the fact that the Viessmann API does not report Pellets consuption values in the free API version:
**Aktuellen Wert "Brennstoffverbrauch" aus ViCare App eintragen** With this node I added a NodeRed UI form that can be used to enter consuption values manually from time to time. The link to that UI form is part of the Grafana dashboard.

The flow includes email notification upon API failures.

Uses an Influx bucket "heating"
![image](https://user-images.githubusercontent.com/13353725/180771640-4393b578-98cd-488e-babd-abf5e20eba6d.png)


## ResolKM2SolarthermieFlow
Uses the Resol APIs to fetch Solarthermie information and publish it to InfluxDB.

For starters you will have to enter your password and IP address in the **set variables** node

Uses an Influx bucket "solar"
![image](https://user-images.githubusercontent.com/13353725/180771444-3a998891-2a20-42f1-b5ab-070026d0c8f5.png)

## PVFlow and PVDashboardFlow
Uses the Fronium Symo APIs to fetch PV information and publish it to 
- Virtual Homee in Homee devices
- InfluxDB
- A NodeRed Dashboard (deprecated - using Influx-Grafana now)

Our house has 2 Wechselrichter so it's a bit more complex. 
The 2nd (lower) one pushes its metrics to flow variables which are then integrated with the metrics from the 1st one.
The 2nd one also tends to show API problems so it' monitored for errors.

The flow  includes email notification upon API failures.

For starters you will have to enter your IP adresses in the **http GET: WR1**  **http GET: WR2** nodes.

Uses an Influx bucket "pv"
![image](https://user-images.githubusercontent.com/13353725/180775201-5f368d1a-8a55-43d7-98b7-e6abaa7e47ea.png)

**Dashboard Flow**
![image](https://user-images.githubusercontent.com/13353725/180775279-583edd28-12bd-466a-b863-af99b367a9bb.png)


