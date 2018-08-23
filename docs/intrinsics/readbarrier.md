---
title: _ReadBarrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadBarrier
dev_langs:
- C++
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e46b64b47aa2f47d5b63aea1231a5f8e8bb274ac
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539493"
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Específicos de Microsoft**  
  
 Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
> [!CAUTION]
>  Los objetos `_ReadBarrier`, las funciones intrínsecas del compilador `_WriteBarrier` y `_ReadWriteBarrier` y la macro `MemoryBarrier` están desusados y no se deben usar. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [std:: atomic\<T >](../standard-library/atomic.md) que se definen en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Para tener acceso de hardware, utilice el [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la opción del compilador la [volátil](../cpp/volatile-cpp.md) palabra clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_ReadBarrier`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El objeto `_ReadBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)