---
title: "_daylight, _dstbias, _timezone y _tzname | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tzname"
  - "_timezone"
  - "timezone"
  - "_daylight"
  - "_tzname"
  - "daylight"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "zonas horarias"
  - "ajustes de hora"
  - "variables de zona horaria"
  - "_tzname (función)"
  - "_daylight (función)"
  - "_timezone (función)"
  - "daylight (función)"
  - "ajustes de hora local"
  - "timezone (función)"
  - "tzname (función)"
  - "variables de zona horaria"
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _daylight, _dstbias, _timezone y _tzname
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_daylight`, `_dstbias`, `_timezone`, y `_tzname` se utilizan en algunas rutinas de hora y fecha de realizar ajustes de la hora local.  Estas variables globales están desusadas para las versiones funcionales más seguras, que se debe usar en lugar de las variables globales.  
  
|Variable global|Equivalente funcional|  
|---------------------|---------------------------|  
|`_daylight`|[\_get\_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[\_get\_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[\_get\_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 Se declaran en Time.h como sigue.  
  
## Sintaxis  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## Comentarios  
 En una llamada a `_ftime`, `localtime`, o `_tzset`, los valores de `_daylight`, de `_dstbias`, de `_timezone`, y de `_tzname` se determina el valor de la variable de entorno `TZ` .  Si no establece explícitamente el valor de `TZ`, `_tzname[0]` y `_tzname[1]` contienen las configuraciones predeterminadas de “PST” y “PDT” respectivamente.  Las funciones de la Tiempo\- manipulación \([\_tzset](../c-runtime-library/reference/tzset.md), [\_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md), y [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)\) intentan establecer los valores de `_daylight`, de `_dstbias` y de `_timezone` consultando el sistema operativo para el valor predeterminado de cada variable.  Los valores de variable global de la zona horaria se muestran en la tabla siguiente.  
  
|Variable|Valor|  
|--------------|-----------|  
|`_daylight`|Distinto de cero si la zona de \(DST\) de horario de verano se especifica en `TZ` o se determina del sistema operativo; de lo contrario, 0.  El valor predeterminado es 1.|  
|`_dstbias`|Desplazamiento al horario de verano.|  
|`_timezone`|Diferencia en segundos entre la hora UTC y la hora local.  El valor predeterminado es 28,800.|  
|`_tzname[0]`|Nombre de la zona horaria derivado de la variable de entorno `TZ` .  El valor predeterminado es "PST".|  
|`_tzname[1]`|El nombre de la zona de DST derivado de la variable de entorno `TZ` .  El valor predeterminado es “PDT” \(horario de verano Pacífico\).|  
  
## Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [\_get\_daylight](../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../c-runtime-library/reference/get-tzname.md)