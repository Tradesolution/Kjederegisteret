# Do you get really old files from Kjederegisteret? How can you move to the new API instead?
In 2021, Tradesolution built a new platform for Kjederegisteret. We changed some datastructures and introduced some new ones. Everything is available through a new and shiny API, but we still provide files with the old datastructures for a limited time period. Switching to the API can cause some pain, but we would like it to be as little as possible. No new datafields will become available in the old files. 

The new api can be found here: https://kjederegisteretapi.tradesolution.no/swagger/index.html

# What has changed?
- Enhet is the main data structure, which is the store/kiosk/school etc. They still have løpenummer as the identity number.
- The concept Kjeder is cleaned up and will only be real Kjeder where enheter share marketing profile like Rema 1000 and Kiwi. In the old files, everything had to be in a kjede, which gave some strange structures for i.e. Innkjøpssamarbeid. We no longer use HKODE, but two different types of kjeder: Markedskjede (product range focus) and Regionalkjede (geographic focus). Enheter are no longer required to be in a kjede, but if they are, they can only be in one type at any given point
- Enhetsgruppering is a new concept introduced to capture groupings of enheter, but they are not limited to only one membership at a time. Currently, we have three types: Innkjøpssamarbeid, Offentlig innkjøp and Grossistgruppering. This allows an enhet to be member of two Innkjøpssamarbeid at the same time. Enheter are not required to be a member of 
- Innkjøpssamarbeid and Kommuner are moved from Kjeder to Enhetsgruppering. Kommuner will use the type Offentlig innkjøp
- Moduler are no longer provided since this geographic information is outdated and not activly maintained 
