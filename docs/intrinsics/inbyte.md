---
title: __inbyte | Microsoft Docs
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
ms.openlocfilehash: 7a503cb71ee1a7121a4770d5a401e33fe14fc649
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716547"
---
# <a name="inbyte"></a>__inbyte
**Específicos de Microsoft**  
  
 Genera el `in` instrucción de devolución de un byte lee desde el puerto especificado por `Port`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
*Puerto*<br/>
[in] Para leer desde el puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Byte leído desde el puerto especificado.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__inbyte`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)