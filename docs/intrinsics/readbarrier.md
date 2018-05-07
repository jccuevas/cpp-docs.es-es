---
title: _ReadBarrier | Documentos de Microsoft
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
ms.openlocfilehash: 5e188089af114abb3e52ef5c0e289f5c8fa013b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Específicos de Microsoft**  
  
 Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
> [!CAUTION]
>  Los objetos `_ReadBarrier`, las funciones intrínsecas del compilador `_WriteBarrier` y `_ReadWriteBarrier` y la macro `MemoryBarrier` están desusados y no se deben usar. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [std:: atomic\<T >](../standard-library/atomic.md) que están definidos en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Para tener acceso de hardware, utilice la [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador junto con el [volátiles](../cpp/volatile-cpp.md) palabra clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_ReadBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El objeto `_ReadBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)