---
title: __shiftright128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 56fbd52709addbba414d6c6fc839baf96f0b2c02
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="shiftright128"></a>__shiftright128
**Específicos de Microsoft**  
  
 Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la derecha según un número de bits especificado por `Shift` y devuelve los 64 bits inferiores del resultado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `LowPart`  
 Los 64 bits inferiores de la cantidad de 128 bits que se va a desplazar.  
  
 [in] `HighPart`  
 Los 64 bits superiores de la cantidad de 128 bits que se va a desplazar.  
  
 [in] `Shift`  
 El número de bits que se va a desplazar.  
  
## <a name="return-value"></a>Valor devuelto  
 Los 64 bits inferiores del resultado.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El valor `Shift` es siempre módulo 64 para que, por ejemplo, si se llama a `__shiftright128(0, 1, 64)`, la función desplace los bits `0` de la parte alta a la derecha y devuelva una parte baja de `0` en vez de `1`, como cabría esperar.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo, vea [__shiftleft128](../intrinsics/shiftleft128.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)