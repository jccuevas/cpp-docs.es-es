---
title: _callnewh | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _callnewh
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
- _callnewh
dev_langs:
- C++
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5754a22af15f8eca1d7352e3d172d141447a2ca4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="callnewh"></a>_callnewh
Llama al *nuevo controlador* instalado actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `size`  
 Cantidad de memoria que el [nuevo operador](../../cpp/new-operator-cpp.md) ha intentado asignar.  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|0|Error: No se instala ningún controlador nuevo o no hay ningún controlador nuevo activo.|  
|1|Operación correcta: El controlador nuevo se instala y activa. Se puede volver a intentar asignar memoria.|  
  
## <a name="exceptions"></a>Excepciones  
 Esta función genera [bad_alloc](../../standard-library/bad-alloc-class.md) si el *nuevo controlador* no se puede localizar.  
  
## <a name="remarks"></a>Comentarios  
 Se llama al *nuevo controlador* si el [nuevo operador](../../cpp/new-operator-cpp.md) no asigna memoria correctamente. El controlador nuevo podría iniciar una acción adecuada, por ejemplo liberar memoria de modo que las asignaciones subsiguientes se realicen correctamente.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|_callnewh|internal.h|  
  
## <a name="see-also"></a>Vea también  
 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md)   
 [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md)