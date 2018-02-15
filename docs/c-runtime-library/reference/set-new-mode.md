---
title: _set_new_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0c49e60201374f2c9cc916d65077c2800ed48ab
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="setnewmode"></a>_set_new_mode
Establece un nuevo modo de controlador para `malloc`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `newhandlermode`  
 Nuevo modo de controlador para `malloc`; el valor válido es 0 o 1.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el modo de controlador anterior establecido para `malloc`. Un valor devuelto de 1 indica que, en caso de error al asignar memoria, `malloc` llamó previamente a la rutina del nuevo controlador, mientras que un valor devuelto de 0 indica lo contrario. Si el `newhandlermode` argumento no es igual a 0 o 1, devuelve -1.  
  
## <a name="remarks"></a>Comentarios  
 La función `_set_new_mode` de C++ establece el nuevo modo de controlador para [malloc](../../c-runtime-library/reference/malloc.md). El nuevo modo de controlador indica si, en caso de error, `malloc` va a llamar a la rutina del nuevo controlador, según lo establecido por [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). De forma predeterminada, `malloc` no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando `malloc` no pueda asignar memoria, `malloc` llame a la rutina del nuevo controlador de la misma forma que hace el operador `new` cuando se produce un error por la misma razón. Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*. Para invalidar el valor predeterminado, llame a:  
  
```  
_set_new_mode(1)  
```  
  
 temprano en el programa o vincúlelo con Newmode.obj (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).  
  
 Esta función valida su parámetro. Si `newhandlermode` es algún valor distinto de 0 o 1, la función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_**`set_new_mode` devuelve -1 y establece `errno` en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_new_mode`|\<new.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [_query_new_mode](../../c-runtime-library/reference/query-new-mode.md)