# Do you get really old files from Kjederegisteret? How can you move to the new API instead?
In 2021, Tradesolution built a new platform for Kjederegisteret. We changed some datastructures and introduced some new ones. Everything is available through a new and shiny API, but we still provide files with the old datastructures for a limited time period. Switching to the API can cause some pain, but we would like it to be as little as possible. No new datafields will become available in the old files. 

The new api can be found here: https://kjederegisteretapi.tradesolution.no/swagger/index.html

# What has changed?
- Enhet is the main data structure, which is the store/kiosk/school etc. They still have løpenummer as their identity field.
- All identity fields are of type string even though løpenummer, GLN, organisasjonsnummer etc look like numbers. This is because they are identifiers and it does not make sense to do arithmetic on them.
- Statistikknummer is introduced as an identifier for groups of enheter that follow eachother in eierskifer (change of owners). Before this was only represented by a chain with each enhet having fields for NesteLøpenummer and ForrigeLøpenummer.   
- The concept Kjeder is cleaned up and will only be real Kjeder where enheter share marketing profile like Rema 1000 and Kiwi. In the old files, everything had to be in a kjede, which gave some strange structures for i.e. Innkjøpssamarbeid. We no longer use HKODE, but two different types of kjeder: Markedskjede (product range focus) and Regionalkjede (geographic focus). Enheter are no longer required to be in a kjede, but if they are, they can only be in one type at any given point
- Enhetsgruppering is a new concept introduced to capture groupings of enheter, but they are not limited to only one membership at a time. Currently, we have three types: Innkjøpssamarbeid, Offentlig innkjøp and Grossistgruppering. This allows an enhet to be member of two Innkjøpssamarbeid at the same time. Enheter are not required to be a member of an enhetsgruppe. Note that enhetsgrupper that have parent enhetsgrupper are not related to any kjeder even though they have the same name. For now, there is a strong correlation between kjeder in an Innkjøpsamarbeid and the names on the groups under enhetsgrupper of type Innkjøpsamarbeid. This is done to ensure backwardscompabiblity with the old files. In the future, all enheter could become member directly in the top node, or the sub groups could be divided into types of enehter etc. I.e. Gressgruppen could have sub groups like Hotels, Resturants and Boats instead of the name of different kjeder. This is entirely up to the Innkjøpssamarbeid and Tradesolution. This means that you should not use the names of the groups to find the kjede. Use instead the concepts of Medlemskjeder and Medlemsgrupper. 
- Innkjøpssamarbeid and Kommuner are moved from Kjeder to Enhetsgruppering. Kommuner will use the type Offentlig innkjøp
- Moduler are no longer provided since this geographic information is outdated and not activly maintained 
