import schedule
import time

def announce():
    print("כל בעלי הצמיד הכחול הזמן במתחם הסתיים!")

# תזמון הכרזה בכל שעה עגולה
schedule.every().hour.at(":00").do(announce)

# תזמון הכרזה בכל חצי שעה
schedule.every().hour.at(":30").do(announce)

while True:
    schedule.run_pending()
    time.sleep(1)
