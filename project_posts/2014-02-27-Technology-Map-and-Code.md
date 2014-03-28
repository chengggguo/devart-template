1. We provide a website to run GAE. Users can choose and book a ‘showtime' and make a 'sequence number'(presents the play order of 7 air inlets), to affect the order of air inlets plumping up air at a certain time.

2. RaspberryPi gets the json data from API of the website at regular time. Based on the ’showtime’ and the ’sequence’ users submitted, it send the data to Arduino. Then Arduino controls the play time and play order of the air inlets.

3. Google calendar gets the ’showtime’ as event time, the ’sequence number’ as event name, then make a agenda as a Gibbon show schedule.