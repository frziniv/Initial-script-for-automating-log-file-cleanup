# Initial-script-for-automating-log-file-cleanup
import os
import time

# --- INITIAL CODE STRING ---
def clean_stale_logs(directory=".", days_old=30):
    """
    Scans a directory for log files and removes those older than a specified number of days.
    """
    now = time.time()
    cutoff = now - (days_old * 86400) # 86400 seconds in a day

    for filename in os.listdir(directory):
import os
import time
import logging # New Import

# --- EDITED CODE STRING ---
# Configure basic logging setup
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')

def clean_stale_logs(directory=".", days_old=30):
    """
    Scans a directory for log files and logs those older than a specified number of days.
    """
    logging.info(f"Starting log cleanup in directory: {directory} for files older than {days_old} days.")
    now = time.time()
    cutoff = now - (days_old * 86400) # 86400 seconds in a day

    for filename in os.listdir(directory):
        full_path = os.path.join(directory, filename)
        if os.path.isfile(full_path) and filename.endswith(".log"):
            if os.stat(full_path).st_mtime < cutoff:
                # Replaced print() with logging.info()
                logging.warning(f"File {filename} at {full_path} is stale. Candidate for archiving/removal.")
    
    logging.info("Log cleanup scan complete.")
# ---------------------------

# Example usage (run this in the file):
# clean_stale_logs("/path/to/your/logs", 60)        if os.path.isfile(full_path) and filename.endswith(".log"):
            # Check if the file was modified before the cutoff time
            if os.stat(full_path).st_mtime < cutoff:
                # In a real scenario, this would be a delete/archive operation
                print(f"File {filename} is stale. Candidate for removal.")
                # os.remove(full_path) # Commented out for safety
# ---------------------------

# Example usage (run this in the file):
# clean_stale_logs("/path/to/your/logs", 60)
