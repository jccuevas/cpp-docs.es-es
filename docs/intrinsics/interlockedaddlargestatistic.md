---
title: _InterlockedAddLargeStatistic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa3a9a88520516051b067d45f4e18a92946c1346
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Específicos de Microsoft**  
  
 Realiza una suma entrelazada en el que el primer operando es un valor de 64 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in, out] `Addend`  
 Un puntero al primer operando a la operación de agregación. El valor al que señala se reemplaza por el resultado de la suma.  
  
 [in] `Value`  
 El segundo operando; valor que se va a agregar al primer operando.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor del segundo operando.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función intrínseca no es atómica porque se implementa como dos independientes instrucciones bloqueadas. Una lectura atómica de 64 bits que se produce en otro subproceso durante la ejecución de este intrínseco podría producir un valor no que se va a leer.  
  
 Esta función se comporta como una barrera de lectura y escritura. Para obtener más información, consulte [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)