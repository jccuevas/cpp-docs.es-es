---
title: __readmsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26fb2637c5a92a430d72e496cabeb8f5749ccaa1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711806"
---
# <a name="readmsr"></a>__readmsr
**Específicos de Microsoft**  
  
 Genera el `rdmsr` instrucción, que lee el registro específicos del modelo especificado por `register` y devuelve su valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
*register*<br/>
[in] El registro específico del modelo para leer.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor en el registro especificado.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__readmsr`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función sólo está disponible en modo kernel y la rutina solo está disponible como intrínseco.  
  
 Para obtener más información, consulte la documentación de AMD.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)