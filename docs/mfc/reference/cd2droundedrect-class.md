---
title: Clase CD2DRoundedRect | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
dev_langs:
- C++
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 5496ad1262246e44871cc540b4021c7fb18216ca
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="cd2droundedrect-class"></a>Clase CD2DRoundedRect
Contenedor para `D2D1_ROUNDED_RECT`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRoundedRect::CD2DRoundedRect](#cd2droundedrect)|Sobrecargado. Construye un `CD2DRoundedRect` objeto `D2D1_ROUNDED_RECT` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_ROUNDED_RECT`  
  
 [CD2DRoundedRect](../../mfc/reference/cd2droundedrect-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2droundedrect"></a>CD2DRoundedRect::CD2DRoundedRect  
 Construye un objeto CD2DRoundedRect del objeto CD2DRectF.  
  
```  
CD2DRoundedRect(
    const CD2DRectF& rectIn,  
    const CD2DSizeF& sizeRadius);  
  
CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);  
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```  
  
### <a name="parameters"></a>Parámetros  
 `rectIn`  
 rectángulo de origen  
  
 `sizeRadius`  
 tamaño de RADIUS  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

