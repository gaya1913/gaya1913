import schedule
import time
import pyttsx3
import itertools

# אתחול מנוע הדיבור
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)  # בחר קול של אישה

# רשימת המשפטים
messages = [
    "כל בעלי הצמיד הכתום, כל בעלי הצמיד הכתום, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד הכתום!",
    "כל בעלי הצמיד הכחול, כל בעלי הצמיד הכחול, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד הכחול!",
    "כל בעלי הצמיד הירוק, כל בעלי הצמיד הירוק, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד הירוק!",
    "כל בעלי הצמיד האדום, כל בעלי הצמיד האדום, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד האדום!",
    "כל בעלי הצמיד הצהוב, כל בעלי הצמיד הצהוב, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד הצהוב!",
    "כל בעלי הצמיד הסגול, כל בעלי הצמיד הסגול, הזמן במתחם הסתיים. מי שרוצה להאריך מוזמן לגשת לקופה. כל בעלי הצצמיד הסגול!",
]

message_cycle = itertools.cycle(messages)

def announce():
    message = next(message_cycle)  
    print(message)
    engine.say(message)    
    engine.runAndWait()

def setup_schedule():
    schedule.every().hour.at(":00").do(announce)

    schedule.every().hour.at(":30").do(announce)

if __name__ == "__main__":
    setup_schedule()

    while True:
        schedule.run_pending()
        time.sleep(1)
