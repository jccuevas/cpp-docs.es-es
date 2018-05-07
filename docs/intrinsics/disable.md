---
title: formas intrínsecas _disable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4359d77f13338e2e007236b0103fd358dffd0ce1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="disable"></a>_disable
**Específicos de Microsoft**  
  
 Deshabilita las interrupciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_disable`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 `_disable` indica al procesador que debe borrar la marca de la interrupción. En sistemas x86, esta función genera la instrucción Borrar marca de interrupción (`cli`).  
  
 Esta función solo está disponible en modo kernel. Si se utiliza en modo de usuario, se produce una excepción de Instrucción privilegiada en tiempo de ejecución.  
  
 En las plataformas ARM, esta rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)