---
title: __inword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indword_cpp
- __indword
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8ed68cad5ba6aa56a4040c62da4570981534d9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538937"
---
# <a name="inword"></a>__inword
**Específicos de Microsoft**  
  
 Lee datos desde el puerto especificado mediante el `in` instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned short __inword(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Port`  
 Para leer desde el puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 La palabra de los datos leídos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__inword`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)