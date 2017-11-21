---
title: RECT estructura-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs: C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d3a33330ace97db19521362384356b58a6c8dca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="rect-structure1"></a>RECT estructura-1
La estructura `RECT` define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>Miembros  
 `left`  
 Especifica la coordenada x de la esquina superior izquierda de un rectángulo.  
  
 `top`  
 Especifica la coordenada y de la esquina superior izquierda de un rectángulo.  
  
 `right`  
 Especifica la coordenada x de la esquina inferior derecha de un rectángulo.  
  
 `bottom`  
 Especifica la coordenada y de la esquina inferior derecha de un rectángulo.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** windef.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)
