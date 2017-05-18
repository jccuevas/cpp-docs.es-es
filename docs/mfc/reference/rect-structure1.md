---
title: Estructura de RECT-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure
- LPRECT structure
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: bc91b22f291f23ed396a054b0c929410718286a3
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="rect-structure1"></a>Estructura de RECT-1
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
 [!code-cpp[NVC_MFC_Utilities&#38;](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** windef.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)

