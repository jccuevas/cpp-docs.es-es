---
title: XFORM (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2d23b3838f1e2dcabb2affb96fa6f18942581ff8
ms.lasthandoff: 02/24/2017

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
 El `XFORM` estructura especifica un espacio del mundo para transformación de espacio en la página. El **eDx** y **eDy** miembros especifican los componentes de traslación horizontal y vertical, respectivamente. En la tabla siguiente se muestra cómo se utilizan los demás miembros, dependiendo de la operación:  
  
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


