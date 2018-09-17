---
title: __writecr3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr3
dev_langs:
- C++
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10acb6af23dffef0a7067883ac5dbac5abd9234f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724267"
---
# <a name="writecr3"></a>__writecr3
**Específicos de Microsoft**  
  
 Escribe el valor `Data` al registro CR3.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void writecr3(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
*Data*<br/>
[in] El valor para escribir en el registro CR3.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__writecr3`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)