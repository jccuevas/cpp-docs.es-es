---
title: fesetexceptflag2 | Microsoft Docs
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
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 2283d258a15fb131367d5d24a921c0a84a31e91d
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="fesetexceptflag"></a>fesetexceptflag
Establece las marcas de estado de punto flotante especificadas en el entorno actual de punto flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstatus`  
 Puntero a un objeto `fexcept_t` que contiene los valores en los que se establecen las marcas de estado de excepción. Es posible que el objeto se haya establecido mediante una llamada anterior a [fegetexceptflag](fegetexceptflag2.md).  
  
 `excepts`  
 Marcas de estado de excepción de punto flotante que se establecen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si todas las marcas de estado de excepción especificadas se establecen correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.  
  
## <a name="remarks"></a>Comentarios  
 La función `fesetexceptflag` establece el estado de las marcas de estado de excepción de punto flotante especificadas por `excepts` en los valores correspondientes establecidos en el objeto `fexcept_t` al que apunta `pstatus`.  No genera las excepciones. El puntero `pstatus` debe apuntar a un objeto `fexcept_t` válido o el comportamiento posterior es indefinido. La función `fesetexceptflag` admite estos valores de macro de excepción en `excepts`, que se definen en \<fenv.h>:  
  
|Macro de excepción|Descripción|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|  
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|  
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|  
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|  
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|  
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|  
  
 El argumento `excepts` puede ser cero, una de las macros de excepción de punto flotante admitidas o la operación OR bit a bit de dos o más de las macros. El efecto de cualquier otro valor de argumento es indefinido.  
  
 Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulte [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`fesetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)
