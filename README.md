# ESP8266_GetLocalTime
A function to replicate the ESP32 GetLocalTime function


bool GetLocalTime(struct tm * info, uint32_t ms) {
  uint32_t start = millis();
  time_t now;
  while ((millis() - start) <= ms) {
    time(&now);
    localtime_r(&now, info);
    if (info->tm_year > (2016 - 1900)) {
      return true;
    }
    delay(10);
  }
  return false;
}
