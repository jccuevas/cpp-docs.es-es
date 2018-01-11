---
title: _set_error_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_error_mode
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
- set_error_mode
- _set_error_mode
dev_langs: C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7987686fb0b9faa03cf4d5e4795116e9f0a608bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="seterrormode"></a>_set_error_mode
Modifica `__error_mode` para determinar una ubicación no predeterminada en donde el tiempo de ejecución de C escribe un mensaje de error si hay un error que podría finalizar el programa.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `modeval`  
 Destino de los mensajes de error.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el valor anterior o -1 si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 Controla el receptor de salida de error estableciendo el valor de `__error_mode`. Por ejemplo, puede dirigir la salida a un error estándar o utilizar La API de `MessageBox`.  
  
 El parámetro `modeval` puede establecerse en uno de los valores siguientes:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_OUT_TO_DEFAULT`|El receptor de errores viene determinado por `__app_type`.|  
|`_OUT_TO_STDERR`|El receptor de errores es un error estándar.|  
|`_OUT_TO_MSGBOX`|El receptor de errores es un cuadro de mensaje.|  
|`_REPORT_ERRMODE`|Notifica el valor actual de `__error_mode`.|  
  
 Si se pasa un valor distinto de los de la lista, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `_set_error_mode` establece `errno` en `EINVAL` y devuelve -1.  
  
 Cuando se usa con un [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md), `_set_error_mode` muestra la instrucción con errores en el cuadro de diálogo y ofrece la posibilidad de elegir el botón `Ignore` para que se pueda seguir ejecutando el programa.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_error_mode`|\<stdlib.h>|  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
```Output  
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Vea también  
 [assert Macro, _assert, _wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)