#importing a Tsv dataset
impressions <- read_tsv("impressions.tsv")
clicks <- read_tsv("clicks.tsv")

#importing a Csv dataset
advertiser <- read_csv("advertiser.csv")
campaigns <- read_csv("campaigns.csv")

#converting the timezone to UTC
for (z in seq_along(impressions$time)){
       a <- as.numeric(impressions$time[z]) #coverting the type of variable to numeric
       a = a/60/60                          #converting time in seconds into hours
       if(impressions$timezone[z] == "Eastern time"){
             a = a - 5   #Eastern time is 5 hours behind UTC
             print(a)
         }else if(impressions$timezone[z] == "Pacific time"){
               a = a - 8 #Pacific time is 8 hours behind UTC
               print(a)
           }
}

#converting the timezone to UTC
for (z in seq_along(clicks$time)){
  a <- as.numeric(clicks$time[z]) #coverting the type of variable to numeric
  a = a/60/60                          #converting time in seconds into hours
  if(clicks$timezone[z] == "Eastern time"){
    a = a - 5   #Eastern time is 5 hours behind UTC
    print(a)
  }else if(clicks$timezone[z] == "Pacific time"){
    a = a - 8 #Pacific time is 8 hours behind UTC
    print(a)
  }
}

#Changing column names to match campaigns
advertiser <- setNames(advertiser, c("advertiser_id", "name"))

#Joining campaigns and advertiser with mutal variable "advertiser_id"
csv <- full_join(campaigns, advertiser, by = "advertiser_id")

#Changing column names to match impressions and clicks
csv <- setNames(csv, c("campaign_id", "advertiser_id", "campaign_name", "budget", "advertiser_name"))

#Joining advertiser and Csv with mutal variable "campaign_I=id"
impressions_processed <- full_join(impressions, csv, by="campaign_id")

#exporting the new impressions dataset to a Csv
write.csv(impressions_processed, 'impressions_processed.csv')

#Joining clicks and csv with mutal variable campaign_id
clicks2 <- full_join(clicks, csv,by = "campaign_id")

#Exporting the new clicks dataset to Csv
write.csv(clicks2, 'clicks_processed.csv')