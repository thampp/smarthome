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

Uses an Influx bucket "heating"


## ResolKM2SolarthermieFlow
Uses the Resol APIs to fetch Solarthermie information and publish it to InfluxDB.

For starters you will have to enter your password and IP address in the **set variables** node

Uses an Influx bucket "solar"


