---
title: fegetround, fesetround2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fegetround
- fesetround
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
dev_langs: C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 544a9e43f029ba03b2ccd40e7ab6fe4fdb1d8127
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround
Obtiene o establece el modo de redondeo de punto flotante actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### <a name="parameters"></a>Parámetros  
 `round_mode`  
 El modo de redondeo que se va a establecer, como una de las macros de redondeo de punto flotante. Si el valor no es igual a una de las macros de redondeo de punto flotante, no se cambiará el modo de redondeo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, `fegetround` devuelve el modo de redondeo como uno de los valores de la macro de redondeo de punto flotante. Devuelve un valor negativo si no se puede determinar el modo de redondeo actual.  
  
 Si se realiza correctamente, `fesetround` devuelve 0. De lo contrario, devuelve un valor distinto de cero.  
  
## <a name="remarks"></a>Comentarios  
 Las operaciones de punto flotante pueden usar uno de los distintos modos de redondeo. Estos controlan en qué dirección se redondean los resultados de las operaciones de punto flotante cuando se almacenan los resultados. Se trata de los nombres y comportamientos de las macros de redondeo de punto flotante que se definen en \<fenv.h>:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|FE_DOWNWARD|Redondeo a infinito negativo.|  
|FE_TONEAREST|Redondeo al más próximo.|  
|FE_TOWARDZERO|Redondeo a cero.|  
|FE_UPWARD|Redondeo a infinito positivo.|  
  
 El comportamiento predeterminado de FE_TONEAREST es redondear los resultados que se encuentran entre valores representables al valor más próximo con un bit menos significativo par (0).  
  
 El modo de redondeo actual afecta a estas operaciones:  
  
-   Las conversiones de cadenas.  
  
-   Los resultados de los operadores aritméticos de punto flotante fuera de las expresiones constantes.  
  
-   Las funciones de redondeo de la biblioteca, como `rint` y `nearbyint`.  
  
-   Los valores devueltos de las funciones matemáticas de la biblioteca estándar.  
  
 El modo de redondeo actual no afecta a estas operaciones:  
  
-   Las funciones de la biblioteca `trunc`, `ceil`, `floor`y `lround` .  
  
-   Las conversiones implícitas de punto flotante a entero, que siempre se redondean a cero.  
  
-   Los resultados de los operadores aritméticos de punto flotante en expresiones constantes, que siempre se redondean al valor más cercano.  
  
 Para usar estas funciones, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulte [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`fegetround`,                `fesetround`|\<fenv.h>|\<cfenv>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint, nearbyintf, nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)