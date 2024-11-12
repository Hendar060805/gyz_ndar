import time
import winsound  # Untuk sistem Windows

def set_alarm(hour, minute, second, sound_duration=1000):
    """
    Setel alarm pada waktu tertentu.
    :param hour: Jam alarm (0-23)
    :param minute: Menit alarm (0-59)
    :param second: Detik alarm (0-59)
    :param sound_duration: Durasi suara alarm dalam milidetik
    """
    # Waktu sekarang
    current_time = time.localtime()
    current_hour = current_time.tm_hour
    current_minute = current_time.tm_min
    current_second = current_time.tm_sec
    
    # Hitung berapa lama lagi alarm akan berbunyi
    alarm_time = (hour * 3600 + minute * 60 + second)
    current_time_in_seconds = (current_hour * 3600 + current_minute * 60 + current_second)
    
    # Tentukan waktu yang tersisa sampai alarm berbunyi
    time_to_wait = alarm_time - current_time_in_seconds
    if time_to_wait < 0:
        time_to_wait += 24 * 3600  # Jika alarm sudah lewat, hitung untuk hari berikutnya
    
    # Tunda hingga waktu alarm
    print(f"Alarm akan berbunyi dalam {time_to_wait} detik.")
    time.sleep(time_to_wait)
    
    # Suara alarm
    print("ALARM BERBUNYI!")
    winsound.Beep(1000, sound_duration)  # Suara beep pada frekuensi 1000Hz, durasi 1 detik

# Setel alarm pada jam tertentu (contoh: jam 7 pagi 30 menit)
set_alarm(7, 30, 0)

