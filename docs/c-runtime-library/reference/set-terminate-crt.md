---
title: set_terminate (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_terminate
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
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eba062bd1b791f055b2ae1c74c2a0107a4039d23
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)
Instala su propia rutina de finalización a la que debe llamar `terminate`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `termFunction`  
 Puntero a una función de finalización que se escribe.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la función anterior registrada por `set_terminate` para que después se pueda restaurar dicha función. Si no se ha establecido ninguna función anterior, el valor devuelto se puede usar para restaurar el comportamiento predeterminado; puede que este valor sea NULL.  
  
## <a name="remarks"></a>Comentarios  
 La función `set_terminate` instala `termFunction` como la función llamada por `terminate`. `set_terminate` se usa con el control de excepciones de C++ y se puede llamar en cualquier momento en el programa antes de que se produzca la excepción. `terminate` llama a `abort` de forma predeterminada. Puede cambiar este comportamiento predeterminado si escribe su propia función de finalización y llama a `set_terminate` con el nombre de esta función como argumento. `terminate` llama a la última función especificada como argumento para `set_terminate`. Después de llevar a cabo cualquier tarea de limpieza deseada, `termFunction` debe salir del programa. En caso contrario (si regresa a su llamador), se llama a `abort`.  
  
 En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.  
  
 El tipo `terminate_function` está definido en EH.H como puntero a una función de finalización definida por el usuario, `termFunction` que devuelve `void`. La función personalizada `termFunction` no puede tomar ningún argumento y no debe volver al llamador. Si es así, se llama a `abort`. Es posible que no se pueda producir una excepción desde `termFunction`.  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  La función `set_terminate` solo funciona fuera del depurador.  
  
 Solo hay un controlador `set_terminate` para todos los archivos EXE y DLL vinculados dinámicamente; incluso si llama a `set_terminate`, es posible que el controlador se reemplace por otro o que esté reemplazando un controlador establecido por otro archivo EXE o DLL.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`set_terminate`|\<eh.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [terminate](../../c-runtime-library/reference/terminate-crt.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)