---
title: Administración del tiempo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c33d22f30275c9d6581d6c1cd97de4ffe68bc08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418346"
---
# <a name="time-management"></a>Administración del tiempo

Use estas funciones para obtener la hora actual y convertirla, ajustarla y almacenarla según sea necesario. La hora actual es la hora del sistema.

 Las rutinas **_ftime** y **localtime** usan la variable de entorno **TZ**. Si no se establece el valor de **TZ**, la biblioteca en tiempo de ejecución intenta usar la información de zona horaria especificada por el sistema operativo. Si esta información no está disponible, estas funciones usan el valor predeterminado de PST8PDT. Para obtener más información sobre **TZ**, consulte [_tzset](../c-runtime-library/reference/tzset.md); consulte también [_daylight, timezone y _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Rutinas de tiempo

|Función|Usar|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Convertir la hora de tipo **struct tm** a cadena de caracteres. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[clock](../c-runtime-library/reference/clock.md)|Devolver el tiempo de reloj transcurrido en el proceso.|
|[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Convertir la hora del tipo **time_t**, **__time32_t** o **__time64_t** a cadena de caracteres. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Calcular la diferencia entre dos horas.|[System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Almacenar la hora actual del sistema en la variable de tipo **struct _timeb** o de tipo **struct __timeb64**. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Definir la hora de modificación del archivo abierto.|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Convertir la hora del tipo **time_t** al **struct tm** o del tipo **__time64_t** al **struct tm**. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Convertir la hora del tipo **time_t** a **struct tm** o del tipo **__time64_t** a **struct tm** con corrección local. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Convertir la hora a un valor de calendario en formato de la Hora del meridiano de Greenwich.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Convertir la hora a un valor de calendario.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Devolver la fecha actual del sistema como cadena. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Dar formato a la cadena de fecha y hora para uso internacional.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s, _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Devolver la hora actual del sistema como cadena. Las versiones de estas funciones con el sufijo **_s** son más seguras.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Obtener la hora actual del sistema como tipo **time_t**, **__time32_t** o como tipo **__time64_t**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Definir variables externas de tiempo desde la variable de tiempo de entorno **TZ**.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Definir la hora de modificación del archivo especificado mediante la hora actual o el valor de hora almacenado en la estructura.|

> [!NOTE]
> En todas las versiones de Microsoft C/C++, excepto Microsoft C/C++ versión 7.0, y en todas las versiones de Visual C++, la función de hora devuelve la hora actual como el número de segundos transcurridos desde la medianoche del 1.° de enero de 1970. En Microsoft C/C++ versión 7.0, el valor **time** devolvió la hora actual como el número de segundos transcurridos desde la medianoche del 31 de diciembre de 1899.

> [!NOTE]
> En versiones de Visual C++ y Microsoft C/C++ anteriores a Visual C++ 2005, el valor **time_t** fue **long** **int** (32 bits) y, por lo tanto, no se pudo usar para fechas después de las 3:14:07 del 19 de enero de 2038, hora UTC. El valor**time_t** ahora es equivalente a **__time64_t** de manera predeterminada, pero si se define **_USE_32BIT_TIME_T**, se cambia **time_t** a **__time32_t** y fuerza a muchas funciones de hora a llamar a las versiones que usan el valor **time_t** de 32 bits. Para obtener más información, consulte [Tipos estándar](../c-runtime-library/standard-types.md) y comentarios en la documentación sobre las funciones individuales de hora.

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
