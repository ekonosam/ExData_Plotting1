library(stringr)
library(lubridate)
library(data.table)
library(tidyverse)
file<- "C:/Users/Level up coaching/Documents/household_power_consumption.txt"
colnam<- unlist(str_split(readLines(file,n=1),";"))
dat <- fread(file, skip = grep("^[1,2]/2/2007",readLines(file))[1]-1,
             nrow= (grep("3/2/2007", readLines(file))[1] - grep("1/2/2007", readLines(file))[1]))
colnames(dat)<- colnam
dat$Time<- dmy_hms(paste(dat$Date, dat$Time))
dat$Date <- dmy(dat$Date)
dat$Index <- seq(length.out=nrow(dat))
length(dat$Global_active_power)

png(filename = "plot3.png",width = 480,height = 480)
par(mfrow=c(1,1),mar=c(3,4,3,3))
with(dat, plot(Index,Sub_metering_1,type = "l",ylab="Global Active Power (kilowatts)",
               cex.lab= 0.8,xaxt="n"))
with(dat, lines(x=Index,y=Sub_metering_2 ,type = "l",ylab="Global Active Power (kilowatts)",
               cex.lab= 0.8,xaxt="n",col="red"))
with(dat, lines(x=Index,y=Sub_metering_3 ,type = "l",ylab="Global Active Power (kilowatts)",
                cex.lab= 0.8,xaxt="n",col="blue"))
legend("topright",legend = c("Sub_metering_1","Sub_metering_2","Sub_metering_3"),col = c("black","red","blue"),lwd=1.5,cex=0.85)
axis(1,at=c(1,1441 ,nrow(dat)), labels=c("Thu","Fri","Sat")) 
dev.off()
