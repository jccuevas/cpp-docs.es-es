---
title: isnan, _isnan, _isnanf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isnan
- _isnanf
- isnan
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs: C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 982760deff4c5e2439c8743aa0de736a24faa02a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="isnan-isnan-isnanf"></a>isnan, _isnan, _isnanf
Comprueba si un determinado valor de punto flotante es un valor NaN (Not a Number).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 Valor de punto flotante que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 En C, la macro `isnan` y las funciones `_isnan` y `_isnanf` devuelven un valor distinto de cero si el argumento `x` es un NaN; de lo contrario, devuelven 0.  
  
 En C++, las funciones de plantilla `isnan` devuelven `true` si el argumento `x` es un NaN; de lo contrario, devuelven `false`.  
  
## <a name="remarks"></a>Comentarios  
 La macro `isnan` de C y las funciones `_isnan` y `_isnanf` prueban el valor de punto flotante *x*, que devuelve un valor distinto de cero si *x* es un valor NaN (Not a Number). Los valores NaN se generan cuando el resultado de una operación de punto flotante no se puede representar con el formato de punto flotante de IEEE 754 para el tipo especificado. Para obtener información sobre cómo se representa un NaN en la salida, vea [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 Cuando se compila como C++, la macro `isnan` no está definida y, en su lugar, se define una función de plantilla `isnan`. Devuelve un valor de tipo `bool` en lugar de un entero.  
  
 Las funciones `_isnan` y `_isnanf` son específicas de Microsoft. La función `_isnanf` solo está disponible cuando se compila para x64.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|  
|-------------|---------------------------|-------------------------------|  
|`isnan`, `_isnanf`|\<math.h>|\<math.h> o \<cmath>|  
|`_isnan`|\<float.h>|\<float.h> o \<cfloat>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [_finite, _finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [_fpclass, _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)