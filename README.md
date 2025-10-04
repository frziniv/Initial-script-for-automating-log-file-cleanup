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
        full_path = os.path.join(directory, filename)
        if os.path.isfile(full_path) and filename.endswith(".log"):
            # Check if the file was modified before the cutoff time
            if os.stat(full_path).st_mtime < cutoff:
                # In a real scenario, this would be a delete/archive operation
                print(f"File {filename} is stale. Candidate for removal.")
                # os.remove(full_path) # Commented out for safety
# ---------------------------

# Example usage (run this in the file):
# clean_stale_logs("/path/to/your/logs", 60)
