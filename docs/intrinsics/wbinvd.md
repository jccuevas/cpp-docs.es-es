---
title: __wbinvd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __wbinvd
dev_langs:
- C++
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccee7703550bff7980e1cf07b30f29d284e2a3a5
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540315"
---
# <a name="wbinvd"></a>__wbinvd
**Específicos de Microsoft**  
  
 Genera la reescritura e invalidan la caché (`wbinvd`) instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __wbinvd(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__wbinvd`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función sólo está disponible en modo kernel con un nivel de privilegios (CPL) de 0, y la rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)