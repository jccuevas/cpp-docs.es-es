---
title: longjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- longjmp
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
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8d6ae9f6207bc0cc42ec2a0749ddfb6253c496f6
ms.lasthandoff: 02/24/2017

---
# <a name="longjmp"></a>longjmp
Restaura el entorno de pila y la configuración regional de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `env`  
 Variable donde se almacena el entorno.  
  
 *value*  
 Valor que se devolverá a la llamada a `setjmp`.  
  
## <a name="remarks"></a>Comentarios  
 La función `longjmp` restaura un entorno de pila y la configuración regional de ejecución que guardó `setjmp` en `env`. `setjmp` y `longjmp` proporcionan una forma de ejecutar un `goto` no local; se suelen usar para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin usar las convenciones normales de llamada y devolución.  
  
 Si se hace una llamada a `setjmp`, el entorno de pila actual se guarda en `env`. Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la llamada `setjmp` correspondiente. La ejecución se reanuda como si se hubiera devuelto *value* mediante la llamada `setjmp`. Los valores de todas las variables (excepto las variables de registro) a las que se puede obtener acceso en la rutina que recibe el control contienen los valores que tenían cuando se llamó a `longjmp`. Los valores de las variables de registro son imprevisibles. El valor devuelto por `setjmp` debe ser distinto de cero. Si *value* se pasa como 0, se sustituye el valor 1 en la devolución real.  
  
 Llame a `longjmp` antes de que vuelva la función que llamó a `setjmp`; en caso contrario, los resultados son impredecibles.  
  
 Observe las siguientes restricciones al usar `longjmp`:  
  
-   No presuponga que los valores de las variables de registro seguirán siendo los mismos. Los valores de las variables de registro de la rutina que llama a `setjmp` podrían no restaurarse a los valores adecuados después de ejecutar `longjmp`.  
  
-   No use `longjmp` para transferir el control fuera de una rutina de control de interrupción a menos que la interrupción sea consecuencia de una excepción de punto flotante. En este caso, se podría devolver un programa desde un controlador de interrupción a través de `longjmp` si primero se reinicializa el paquete matemático de punto flotante mediante una llamada a `_fpreset`.  
  
     **Nota** Tenga cuidado al usar `setjmp` y `longjmp` en los programas de C++. Dado que estas funciones no admiten la semántica de objetos de C++, es más seguro usar el mecanismo de control de excepciones de C++.  
  
 Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`longjmp`|\<setjmp.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_pfreset](../../c-runtime-library/reference/fpreset.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)
