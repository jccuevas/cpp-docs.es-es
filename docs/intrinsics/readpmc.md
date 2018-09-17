---
title: __readpmc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readpmc
dev_langs:
- C++
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0a5a172a7b0f8a309f1d8fd0762e098dc5d416a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720036"
---
# <a name="readpmc"></a>__readpmc
**Específicos de Microsoft**  
  
 Genera el `rdpmc` instrucción, que lee la supervisión especificado por el contador de rendimiento `counter`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __readpmc(   
   unsigned long counter   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
*Contador*<br/>
[in] El contador de rendimiento para leer.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor del contador de rendimiento especificado.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__readpmc`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función intrínseca está disponible en modo de kernel solo, y la rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)