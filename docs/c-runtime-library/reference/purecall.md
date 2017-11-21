---
title: _purecall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs: C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c475c66c92dec7990aa8056a1791c8eeb87d6afa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="purecall"></a>_purecall
Controlador de errores predeterminado de llamadas de función virtual pura. El compilador genera un código para llamar a esta función cuando se llama a una función miembro virtual pura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función `_purecall` es un detalle de implementación específico de Microsoft del compilador de Microsoft Visual C++. Esta función no está diseñada para ser llamada directamente por el código; además, no tiene ninguna declaración de encabezado pública. Se documenta aquí porque se trata de una exportación pública de la biblioteca en tiempo de ejecución de C.  
  
 Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. El compilador genera un código para invocar la función del controlador de errores `_purecall` cuando se llama a una función virtual pura. De forma predeterminada, `_purecall` finaliza el programa. Antes de finalizar, la función `_purecall` invoca una función `_purecall_handler` en el caso de que se haya establecido alguna para el proceso. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tenga la firma `_purecall_handler`; luego, use [_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) para convertirlo en el controlador actual.  
  
## <a name="requirements"></a>Requisitos  
 La función `_purecall` no tiene ninguna declaración de encabezado. La typedef `_purecall_handler` se define en \<stdlib.h>.  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler, _set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)