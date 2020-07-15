library(stringr)
library(lubridate)
library(data.table)
library(tidyverse)
file<- "C:/Users/Level up coaching/Documents/household_power_consumption.txt"
colnam<- unlist(str_split(readLines(file,n=1),";"))
dat <- fread(file, skip = grep("^[1,2]/2/2007",readLines(file))[1]-1,
             nrow= (grep("3/2/2007", readLines(file))[1] - grep("1/2/2007", readLines(file))[1]))
colnames(dat)<- colnam
dat$Date <- dmy(dat$Date)

png(filename = "plot1.png",width = 480,height = 480)
par(mfrow=c(1,1),mar=c(4,4,3,3))
with(dat, hist(Global_active_power,col="red",xlab="Global Active Power (kilowatts)",
               main= "Global Active Power", cex.lab= 0.8))
dev.off()
