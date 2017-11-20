---
title: "Categorías de configuración regional | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
dev_langs: C++
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dd57f24bd6d790cc03c3e5bbb1e58ec45eee86e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="locale-categories"></a>Categorías de configuración regional
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <locale.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las categorías de configuración regional son constantes de manifiesto utilizadas por las rutinas de localización para especificar qué parte de la información de configuración regional de un programa se usará. La configuración regional hace referencia al lugar o país/región para el que se pueden personalizar algunos aspectos del programa. Entre las áreas dependientes de la configuración regional se encuentran, por ejemplo, el formato de fechas o el formato de presentación de valores de moneda.  
  
|Categoría de configuración regional|Partes del programa afectadas|  
|---------------------|-------------------------------|  
|`LC_ALL`|Todos los comportamientos específicos de la configuración regional (todas las categorías)|  
|`LC_COLLATE`|Comportamiento de las funciones `strcoll` y `strxfrm`|  
|`LC_CTYPE`|Comportamiento de las funciones de control de caracteres (excepto **isdigit**, `isxdigit`, `mbstowcs` y `mbtowc`, que no se ven afectadas)|  
|`LC_MAX`|Igual a `LC_TIME`|  
|`LC_MIN`|Igual a `LC_ALL`|  
|`LC_MONETARY`|Información de formato de moneda devuelta por la función `localeconv`|  
|`LC_NUMERIC`|Carácter de separador decimal para las rutinas de salida con formato (por ejemplo, `printf`), para las rutinas de conversión de datos y para la información de formato no monetaria devuelta por la función `localeconv`|  
|`LC_TIME`|Comportamiento de la función `strftime`|  
  
 Vea [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener un ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll (Funciones)](../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)