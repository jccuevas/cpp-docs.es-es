---
title: feholdexcept2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
dev_langs:
- C++
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbfef5db5871740744e370d7e1ac86cf7abac8ac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="feholdexcept"></a>feholdexcept
Guarda el entorno actual de punto flotante en el objeto especificado, borra las marcas de estado de punto flotante y, si es posible, coloca el entorno de punto flotante en modo continuo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `penv`  
 Puntero a un objeto `fenv_t` que contiene una copia del entorno de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si y solo si la función es capaz de activar correctamente el control de excepciones de punto flotante sin interrupciones.  
  
## <a name="remarks"></a>Comentarios  
 La función `feholdexcept` se usa para almacenar el estado actual del entorno de punto flotante en el objeto `fenv_t` al que apunta `penv` y para establecer el entorno de modo que no se interrumpa la ejecución de excepciones de punto flotante. Esto se conoce como modo continuo.  Este modo continúa hasta que el entorno se restaura mediante [fesetenv](fesetenv1.md) o [feupdateenv](../../c-runtime-library/reference/feupdateenv.md).  
  
 Puede usar esta función al principio de una subrutina que tenga que ocultar una o varias excepciones de punto flotante del autor de llamada. Para informar de una excepción, basta con que borre las excepciones no deseadas mediante [feclearexcept,](../../c-runtime-library/reference/feclearexcept1.md) y luego finalice el modo continuo con una llamada a `feupdateenv`.  
  
 Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h>|\<cfenv>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](fesetenv1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)