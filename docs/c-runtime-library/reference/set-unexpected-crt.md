---
title: set_unexpected (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_unexpected
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
- set_unexpected
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edc1d3b96ee5b52d349b30434932d2c9770267b4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)
Instala la función de finalización a la que debe llamar `unexpected`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `unexpFunction`  
 Puntero a una función que se escribe para reemplazar la función `unexpected`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la función de finalización anterior registrada por `_set_unexpected` para que después se pueda restaurar dicha función. Si no se ha establecido ninguna función anterior, el valor devuelto se puede usar para restaurar el comportamiento predeterminado; puede que este valor sea NULL.  
  
## <a name="remarks"></a>Comentarios  
 La función `set_unexpected` instala `unexpFunction` como la función llamada por `unexpected`. `unexpected` no se usa en la implementación actual del control de excepciones de C++. El tipo `unexpected_function` se define en EH.H como puntero a una función inesperada definida por el usuario, `unexpFunction` que devuelve `void`. La función personalizada `unexpFunction` no debe volver al llamador.  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 De forma predeterminada, `unexpected` llama a `terminate`. Puede cambiar este comportamiento predeterminado si escribe su propia función de finalización y llama a `set_unexpected` con el nombre de esta función como argumento. `unexpected` llama a la última función especificada como argumento para `set_unexpected`.  
  
 A diferencia de la función de terminación personalizada instalada mediante una llamada a `set_terminate`, se puede producir una excepción desde `unexpFunction`.  
  
 En un entorno multiproceso, las funciones inesperadas se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función inesperada. Por lo tanto, cada subproceso se encarga de su propio control inesperado.  
  
 En la implementación actual de Microsoft sobre el control de excepciones de C++, `unexpected` llama a `terminate` de forma predeterminada; la biblioteca de tiempo de ejecución del control de excepciones nunca la llama. No hay ninguna ventaja particular si se llama a `unexpected` en vez de llamar a `terminate`.  
  
 Solo hay un controlador `set_unexpected` para todos los archivos EXE y DLL vinculados dinámicamente; incluso si se llama a `set_unexpected`, es posible que el controlador se reemplace por otro establecido por otro archivo EXE o DLL.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`set_unexpected`|\<eh.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)