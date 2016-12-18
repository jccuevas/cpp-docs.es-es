---
title: "vprintf (Funciones) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "vprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "texto con formato [C++]"
  - "vprintf (función)"
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vprintf (Funciones)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de las funciones de `vprintf` contiene un puntero a una lista de argumentos, los formatos y escribe los datos especificados a un destino determinado.  Las funciones difieren en la validación de parámetros realizada, si las funciones toman de ancho o cadenas de caracteres de solo\- byte, el destino de salida, y compatibilidad para especificar el orden en el que los parámetros se utilizan en la cadena de formato.  
  
|||  
|-|-|  
|[\_vcprintf, \_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_vfprintf\_p, \_vfprintf\_p\_l, \_vfwprintf\_p, \_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf\_s, \_vfprintf\_s\_l, vfwprintf\_s, \_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[\_vprintf\_p, \_vprintf\_p\_l, \_vwprintf\_p, \_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf\_s, \_vprintf\_s\_l, vwprintf\_s, \_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[\_vsprintf\_p, \_vsprintf\_p\_l, \_vswprintf\_p, \_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf\_s, \_vsprintf\_s\_l, vswprintf\_s, \_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[\_vscprintf, \_vscprintf\_l, \_vscwprintf, \_vscwprintf\_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[\_vsnprintf, \_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## Comentarios  
 Las funciones de `vprintf` son similares a las funciones de equivalente como se muestra en la tabla siguiente.  Sin embargo, cada función de `vprintf` acepta un puntero a una lista de argumentos, mientras que cada una de las funciones de homólogo acepta una lista de argumentos.  
  
 Estas funciones da formato a los datos de salida a los destinos como sigue.  
  
|Función|Función de equivalente|Destino de salida|Validación de parámetros|Compatibilidad de parámetro posicional|  
|-------------|----------------------------|-----------------------|------------------------------|--------------------------------------------|  
|`_vcprintf`|[\_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|consola|Comprobación de null.|no|  
|`_vcwprintf`|[\_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|consola|Comprobación de null.|no|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Comprobación de null.|no|  
|**vfprintf\_p**|[fprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Comprobación de formato null y válido.|sí|  
|`vfprintf_s`|[fprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Comprobación de formato null y válido.|no|  
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Comprobación de null.|no|  
|**vfwprintf\_p**|[fwprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Comprobación de formato null y válido.|sí|  
|`vfwprintf_s`|[fwprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Comprobación de formato null y válido.|no|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Comprobación de null.|no|  
|**vprintf\_p**|[printf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Comprobación de formato null y válido.|sí|  
|`vprintf_s`|[printf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Comprobación de formato null y válido.|no|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Comprobación de null.|no|  
|**vwprintf\_p**|[wprintf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Comprobación de formato null y válido.|sí|  
|`vwprintf_s`|[wprintf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Comprobación de formato null y válido.|no|  
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
|**vsprintf\_p**|[sprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|memoria designada por *el búfer*|Comprobación de formato null y válido.|sí|  
|`vsprintf_s`|[sprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|memoria designada por *el búfer*|Comprobación de formato null y válido.|no|  
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
|**vswprintf\_p**|[swprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|memoria designada por *el búfer*|Comprobación de formato null y válido.|sí|  
|`vswprintf_s`|[swprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|memoria designada por *el búfer*|Comprobación de formato null y válido.|no|  
|`_vscprintf`|[\_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
|`_vscwprintf`|[\_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
|`_vsnprintf`|[\_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
|`_vsnwprintf`|[\_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|memoria designada por *el búfer*|Comprobación de null.|no|  
  
 El argumento de `argptr` ha escrito `va_list`, que se define en VARARGS.H y STDARG.H.  La variable de `argptr` debe inicializarse por **va\_start,** y se puede restablecer por las llamadas subsiguientes de `va_arg` ; puntos de `argptr` después al principio de una lista de argumentos que se convierten y transmitidos para la salida según las especificaciones correspondientes en el argumento *de formato* .  *el formato* tiene el mismo formato y función que el argumento *de formato* para [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  Ninguna de estas funciones invocan `va_end`.  Para obtener una descripción completa de cada función de `vprintf` , vea la descripción de la función de equivalente como se muestra en la tabla anterior.  
  
 `_vsnprintf` diferencia de **vsprintf** en que escribe no más de bytes *count* *en el búfer*.  
  
 Las versiones de estas funciones con el infijo de **v** en el nombre son versiones de caracteres anchos de las funciones correspondientes sin el infijo de **v** ; en cada una de estas funciones de carácter ancho, *el búfer* y *el formato* son cadenas de caracteres.  Si no, cada función de carácter ancho se comporta de forma idéntica a la función de equivalente de SBCS.  
  
 Las versiones de estas funciones con **\_s** y los sufijos de **\_p** son las versiones más seguras.  Estas versiones validan las cadenas de formato y generará una excepción si la cadena de formato no está bien formada \(por ejemplo, si se utilizan caracteres de formato no válidos\).  
  
 Las versiones de estas funciones con el sufijo de **\_p** proporcionan la capacidad de especificar el orden en el que los argumentos proporcionados se sustituyen en la cadena de formato.  Para obtener más información, vea [printf\_p \(Parámetros de posición\)](../c-runtime-library/printf-p-positional-parameters.md).  
  
 Para **vsprintf**, `vswprintf`, `_vsnprintf` y `_vsnwprintf`, si la copia aparece entre cadenas superpuestas, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Asegúrese de que *el formato* no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  Si usó las versiones seguras de estas funciones \(los sufijos de **\_s** o de **\_p** \), una cadena de formato usuario\- proporcionada podría desencadenar una excepción no válida de parámetro si la cadena usuario\- proporcionada contiene caracteres de formato no válidos.  
  
## Vea también  
 [E\/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)