---
title: __inbyte | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inbyte
- __inbyte_cpp
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad2e02d4e1bc1ee5d1694769b2ec217cd7acbaba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="inbyte"></a>__inbyte
**Específicos de Microsoft**  
  
 Genera el `in` instrucción, devolver un byte lee desde el puerto especificado por `Port`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Port`  
 El puerto que leer.  
  
## <a name="return-value"></a>Valor devuelto  
 Byte leído desde el puerto especificado.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__inbyte`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)