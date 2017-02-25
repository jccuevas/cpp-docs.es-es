---
title: "Administraci&#243;n del tiempo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fechas, miembros de la biblioteca en tiempo de ejecución"
  - "tiempo, administración del tiempo"
  - "funciones de fecha"
  - "funciones de tiempo"
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# Administraci&#243;n del tiempo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Use estas funciones para obtener la hora actual y convertirla, ajustarla y almacenarla según sea necesario. La hora actual es la hora del sistema.  
  
 Las rutinas `_ftime` y `localtime` usan la variable de entorno `TZ`. Si no se establece el valor de `TZ`, la biblioteca de tiempo de ejecución intenta usar la información de zona horaria especificada por el sistema operativo. Si esta información no está disponible, estas funciones usan el valor predeterminado de PST8PDT. Para obtener más información sobre `TZ`, consulte [\_tzset](../c-runtime-library/reference/tzset.md); consulte también [\_daylight, timezone, and \_tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
### Rutinas de tiempo  
  
|Función|Uso|Equivalente de .NET Framework|  
|-------------|---------|-----------------------------------|  
|[asctime, \_wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime\_s, \_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Convertir la hora de tipo `struct tm` a cadena de caracteres. Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[clock](../c-runtime-library/reference/clock.md)|Devolver el tiempo de reloj transcurrido en el proceso.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [\_ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Convertir la hora de tipo `time_t`, `__time32_t` o `__time64_t` a cadena de caracteres. Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)|  
|[difftime, \_difftime32, \_difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Calcular la diferencia entre dos horas.|[System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[\_ftime, \_ftime32, \_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Almacenar la hora actual del sistema en la variable de tipo `struct _timeb` o de tipo `struct``__timeb64` Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)|  
|[\_futime, \_futime32, \_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Definir la hora de modificación del archivo abierto.|[System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx), [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx), [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)|  
|[gmtime, \_gmtime32, \_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Convertir la hora del tipo `time_t` al `struct tm` o del tipo `__time64_t` al `struct tm`.Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx), [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[localtime, \_localtime32, \_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime\_s, \_localtime32\_s, \_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Convertir la hora de tipo `time_t` a `struct tm` o del tipo `__time64_t` a `struct tm` con corrección local. Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)|  
|[\_mkgmtime, \_mkgmtime32, \_mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Convertir la hora a un valor de calendario en formato de la Hora del meridiano de Greenwich.|[System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[mktime, \_mktime32, \_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Convertir la hora a un valor de calendario.|[System::DateTime::DateTime](Overload:System.DateTime.)|  
|[\_strdate, \_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [\_strdate\_s, \_wstrdate\_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Devolver la fecha actual del sistema como cadena. Las versiones de estas funciones con el sufijo `_s` son más seguras.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Dar formato a la cadena de fecha y hora para uso internacional.|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[\_strtime, \_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [\_strtime\_s, \_wstrtime\_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Devolver la hora actual del sistema como cadena. Las versiones de estas funciones con el sufijo `_s` son más seguras.|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[time, \_time32, \_time64](../c-runtime-library/reference/time-time32-time64.md)|Obtener la hora actual del sistema como tipo `time_t`, `__time32_t` o como tipo `__time64_t`.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_tzset](../c-runtime-library/reference/tzset.md)|Definir variables externas de tiempo desde la variable de tiempo de entorno `TZ`.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_utime, \_utime32, \_utime64, \_wutime, \_wutime32, \_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Definir la hora de modificación del archivo especificado mediante la hora actual o el valor de hora almacenado en la estructura.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
> [!NOTE]
>  En todas las versiones de Microsoft C\/C\+\+, excepto Microsoft C\/C\+\+ versión 7.0, y en todas las versiones de Visual C\+\+, la función de hora devuelve la hora actual como el número de segundos transcurridos desde la medianoche del 1.° de enero de 1970. En Microsoft C\/C\+\+ versión 7.0, el valor `time` devolvió la hora actual como el número de segundos transcurridos desde la medianoche del 31 de diciembre de 1899.  
  
> [!NOTE]
>  En versiones de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] y Microsoft C\/C\+\+ anteriores a Visual C\+\+ 2005, el valor `time_t` fue `long int` \(32 bits\) y, por lo tanto, no se pudo usar para fechas después de las 3:14:07 del 19 de enero de 2038, hora UTC. El valor `time_t` ahora es equivalente a `__time64_t` de manera predeterminada, pero si se define `_USE_32BIT_TIME_T` , se cambia `time_t` a `__time32_t` y fuerza a muchas funciones de hora a llamar a las versiones que usan el valor `time_t` de 32 bits. Para obtener más información, consulte [Tipos estándar](../c-runtime-library/standard-types.md) y comentarios en la documentación sobre las funciones individuales de hora.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)