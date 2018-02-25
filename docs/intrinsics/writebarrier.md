---
title: _WriteBarrier | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _WriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fda8963e89086a2b1655b7dbe3d3b95aca24a7df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="writebarrier"></a>_WriteBarrier
**Específicos de Microsoft**  
  
 Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
> [!CAUTION]
>  Los objetos `_ReadBarrier`, las funciones intrínsecas del compilador `_WriteBarrier` y `_ReadWriteBarrier` y la macro `MemoryBarrier` están desusados y no se deben usar. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [std:: atomic\<T >](../standard-library/atomic.md), que se definen en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Para tener acceso de hardware, utilice la [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador junto con el [volátiles](../cpp/volatile-cpp.md) palabra clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _WriteBarrier(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_WriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El objeto `_WriteBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)   
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)