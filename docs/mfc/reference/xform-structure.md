---
title: XFORM (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f6f7121b5cc93c3f8f6f34f22d16cef888bbf15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="xform-structure"></a>XFORM (Estructura)
El `XFORM` estructura tiene el formato siguiente:  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>Comentarios  
 El `XFORM` estructura especifica un espacio universal para la transformación de espacio en la página. El **eDx** y **eDy** miembros especifican los componentes de traducción horizontal y vertical, respectivamente. En la tabla siguiente se muestra cómo se utilizan los demás miembros, dependiendo de la operación:  
  
|Operación|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|Coseno del ángulo de giro|Seno del ángulo de giro|Negativo seno del ángulo de giro|Coseno del ángulo de giro|  
|**Ajuste de escala**|Componente de escala horizontal|Nothing|Nothing|Componente de escala vertical|  
|**Recorte**|Nothing|Constante de proporcionalidad horizontal|Constante de proporcionalidad vertical|Nothing|  
|**Reflexión**|Componente de reflexión horizontal|Nothing|Nothing|Componente de reflexión vertical|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

