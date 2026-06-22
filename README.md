FILE_NAME = "study_log.json"

def log_session():
    subject = input("What subject did you study? ")
    hours = input("How many hours? ")
    date = datetime.date.today().strftime("%Y-%m-%d")

    entry = {"date": date, "subject": subject, "hours": hours}

    # Load existing data or create new list
    if os.path.exists(FILE_NAME):
        with open(FILE_NAME, "r") as file:
            data = json.load(file)
    else:
        data = []

    data.append(entry)

    # Save back to file
    with open(FILE_NAME, "w") as file:
        json.dump(data, file, indent=4)
    
    print(f"Logged {hours} hours of {subject} for {date}!")

if __name__ == "__main__":
    print("--- Welcome to your Study Tracker ---")
    log_session()
