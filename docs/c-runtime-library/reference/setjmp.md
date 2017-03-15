---
title: setjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- setjmp
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
apitype: DLLExport
f1_keywords:
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d13a24974a6c722301c6361a13f9d9178cd70220
ms.lasthandoff: 02/24/2017

---
# <a name="setjmp"></a>setjmp
Guarda el estado actual del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `env`  
 Variable donde se almacena el entorno.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 después de guardar el entorno de pila. Si se devuelve `setjmp` como resultado de una llamada a `longjmp`, devuelve el argumento `value` de `longjmp`; si el argumento `value` de `longjmp` es 0, `setjmp` devuelve 1. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 La función `setjmp` guarda un entorno de pila, que se puede restaurar posteriormente usando `longjmp`. Cuando se usan conjuntamente, `setjmp` y `longjmp` proporcionan una forma de ejecutar un `goto` no local. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones habituales de llamada o devolución.  
  
 Una llamada a `setjmp` guarda el entorno de pila actual en `env`. Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la llamada `setjmp` correspondiente. Todas las variables (excepto las variables de registro) a las que se puede obtener acceso en la rutina que recibe el control contienen los valores que tenían cuando se llamó a `longjmp`.  
  
 No se puede usar `setjmp` para pasar del código nativo al código administrado.  
  
 **Nota** `setjmp` y `longjmp` no admiten la semántica de objetos de C++. En los programas de C++, use el mecanismo de control de excepciones de C++.  
  
 Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_pfreset](../../c-runtime-library/reference/fpreset.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)
