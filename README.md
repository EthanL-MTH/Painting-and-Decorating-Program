# Painting-and-Decorating-Program
For this program the task was to create a software to calculate the paint required, the cost and total paint area for various different rooms. It require the dimensions for the height and width of the walls, doors and windows. It will then calculate and print an itemized bill.

#Intro using a range check to make sure the value is between 1-20
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
print("Welcome, this programme is designed for rooms with square walls, (Quantities between 1-20, for all verbal answer's use lowercase otherwise it will be logged as 'No') T&C applied.")
wallNum = int(input("Please input the number of walls: "))
while True:
    if wallNum in range(1, 21):
        print("Your number is acceptable, please continue.")
        wallNumVer = wallNum
        break
    else:
        print("Your number is invalid you can only use numbers between 1-20, please restart the programme.")
        wallNum = int(input("Please input the number of walls: "))
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")

#The user inputs the amount of walls and their lengths (The walls height are going to be the same) using a while loops increasing i by one each loop until i is <= the number of walls while adding it to a list
i=1
wallHeight = float(input("What are all of the walls heights: "))
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
lengthList = []
while i <= wallNumVer:
    print("For the",i,"wall")
    wallLength = float(input("What the length of the wall: "))
    area = float(wallLength*wallHeight)
    lengthList.insert(i,(int(area)))
    i+=1
    print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
totalWallArea = sum(lengthList)

#User can choose whether there is a door or not and its length
doorYN = str(input("Is there a door: "))
if doorYN == "yes":
    doorHeight = input("What is the height of the door: ")
    doorLength = input("What is the length of the door: ")
    doorArea = float(doorHeight+doorLength)
else:
    doorArea=0

#Basically the walls and door programme combined
l=1
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
windowYN = str(input("Are there windows: "))
windowList = []
if windowYN == "yes":
    windowNum = float(input("How many windows are there: "))
    print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
    while l <= windowNum:
        print("For the",l,"window")
        windowHeight = float(input("What is the height of the window: "))
        windowLength = float(input("What is the length of the window: "))
        winArea = float(windowLength*windowHeight)
        windowList.insert(l,(int(winArea)))
        l+=1
        print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
else:
    totalwindArea = 0
totalWindArea = sum(windowList)

#The calc for the total paint area using the lists created in the while loops, also the litre to meter ratio is 1-5
totalPaintArea = int(totalWallArea-doorArea-totalWindArea)
litreReq=totalPaintArea//5

#The one litre remainder is going to be remTwoLitr just to save a line of code
fiveTinReq = litreReq//5
remFiveLitr = litreReq%5
threeTinReq = remFiveLitr//3
remThreeLitr = remFiveLitr%3
twoTinReq = remThreeLitr//2
remTwoLitr = remThreeLitr%2

#Cost of tins are -> 5 litre paint = £50, 3 litre paint = £35, 2 litre paint = £25, 1 litre = £15 | key | fTCost == five tin cost, etc.
fTCost = float(fiveTinReq*50)
thTCost = float(threeTinReq*35)
twTCost = float(twoTinReq*25)
oTCost = float(remTwoLitr*15)
totalPaintCost = int(fTCost+thTCost+twTCost+oTCost)
labourCost = int(totalPaintArea*5)
totalCost = int(labourCost+totalPaintCost)

#Finally the itemised bill which is just a bunch of print statements with some the variables I have used
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
print("Thank you for using our service, your itemised bill will be...")
print(f"£{fTCost}, for {fiveTinReq} five litre tins")
print(f"£{thTCost}, for {threeTinReq} three litre tins")
print(f"£{twTCost}, for {twoTinReq} two litre tins")
print(f"£{oTCost}, for {remTwoLitr} one litre tins")
print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
print(f"The total for tins £{totalPaintCost}")
print(f"The labour cost is £{labourCost}")
print(f"Your total bill is £{totalCost}")
