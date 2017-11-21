---
title: _Habilitar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _enable
- _enable_cpp
dev_langs: C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e839a70f106ec83c9d2ee786c20f68817e0d4be6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="enable"></a>_enable
**Específicos de Microsoft**  
  
 Habilita las interrupciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _enable(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_enable`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 `_enable` indica al procesador que establezca el indicador de interrupción. En sistemas x86, esta función genera la instrucción Establecer marca de interrupción (`sti`).  
  
 Esta función solo está disponible en modo kernel. Si se utiliza en modo de usuario, se produce una excepción Instrucción privilegiada.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)