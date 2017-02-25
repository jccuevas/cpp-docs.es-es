---
title: "Categor&#237;as de configuraci&#243;n regional | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LC_MAX"
  - "LC_MIN"
  - "LC_MONETARY"
  - "LC_TIME"
  - "LC_NUMERIC"
  - "LC_COLLATE"
  - "LC_CTYPE"
  - "LC_ALL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LC_ALL (constante)"
  - "LC_COLLATE (constante)"
  - "LC_CTYPE (constante)"
  - "LC_MAX (constante)"
  - "LC_MIN (constante)"
  - "LC_MONETARY (constante)"
  - "LC_NUMERIC (constante)"
  - "LC_TIME (constante)"
  - "constantes de configuración regional"
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Categor&#237;as de configuraci&#243;n regional
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <locale.h>  
  
```  
  
## Comentarios  
 Las categorías de configuración regional son constantes de manifiesto utilizadas por las rutinas de localización para especificar utilizarán a qué parte de la información de configuración regional de un programa.  La configuración regional hace referencia al lugar \(o al país o región\) para el que ciertos aspectos del programa se pueden personalizar.  Incluyen Configuración regional\- dependiente de las áreas, por ejemplo, el formato de fechas y el formato de presentación de valores de moneda.  
  
|Categoría de la configuración regional|Elementos del programa afectadas|  
|--------------------------------------------|--------------------------------------|  
|`LC_ALL`|Todo el comportamiento configuración regional\-específico \(todas las categorías\)|  
|`LC_COLLATE`|Comportamiento de `strcoll` y las funciones de `strxfrm`|  
|`LC_CTYPE`|El comportamiento de carácter\- administrar funciona \(excepto **isdigit**, `isxdigit`, `mbstowcs`, y `mbtowc`, que no son afectada\)|  
|`LC_MAX`|Igual que `LC_TIME`|  
|`LC_MIN`|Igual que `LC_ALL`|  
|`LC_MONETARY`|Información monetaria de formato devuelta por la función de `localeconv`|  
|`LC_NUMERIC`|Carácter de separador decimal para las rutinas con formato de salida \(por ejemplo, `printf`\), rutinas de conversión de datos, y la información no monetaria de formato devuelta por la función de `localeconv`|  
|`LC_TIME`|Comportamiento de la función de `strftime`|  
  
 Vea [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener un ejemplo.  
  
## Vea también  
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll \(Funciones\)](../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)