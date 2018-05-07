---
title: Enumeración de Cmfcimagepaintarea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef036c1d619bf85e21edafbd20f20cc27c7c12d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE (Enumeración)
Especifica un modo de dibujo que se utiliza para modificar una imagen en un cuadro de diálogo del editor de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum IMAGE_EDIT_MODE  
{  
    IMAGE_EDIT_MODE_PEN = 0,  
    IMAGE_EDIT_MODE_FILL, 
    IMAGE_EDIT_MODE_LINE, 
    IMAGE_EDIT_MODE_RECT, 
    IMAGE_EDIT_MODE_ELLIPSE, 
    IMAGE_EDIT_MODE_COLOR 
};  
```  
  
## <a name="members"></a>Miembros  
  
|||  
|-|-|  
|Name|Descripción|  
|`IMAGE_EDIT_MODE_PEN`|Utilizado para dibujar píxeles individuales.|  
|`IMAGE_EDIT_MODE_FILL`|Se usa para rellenar todas las áreas adyacentes que contienen el color en la ubicación actual del cursor.|  
|`IMAGE_EDIT_MODE_LINE`|Se utiliza para dibujar una línea.|  
|`IMAGE_EDIT_MODE_RECT`|Se utiliza para dibujar un rectángulo.|  
|`IMAGE_EDIT_MODE_ELLIPSE`|Se utiliza para dibujar una elipse.|  
|`IMAGE_EDIT_MODE_COLOR`|Se usa para establecer el color actual en el color en la ubicación actual del cursor.|  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCImagePaintArea` y `CMFCImageEditorDialog` clases utilizan esta enumeración para establecer el modo de dibujo actual. El modo de dibujo y el color actual se usan para modificar el área de imagen en un cuadro de diálogo del editor de imágenes. Para obtener más información acerca de `CMFCImagePaintArea` y `CMFCImageEditorDialog`, consulte [CMFCImagePaintArea clase](../../mfc/reference/cmfcimagepaintarea-class.md) y [CMFCImageEditorDialog clase](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
 Cuando se selecciona un color de una imagen mediante la `IMAGE_EDIT_MODE_COLOR` modo de dibujo, el marco de trabajo establece el modo de dibujo actual en `IMAGE_EDIT_MODE_PEN`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afximagepaintarea.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea (clase)](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog (clase)](../../mfc/reference/cmfcimageeditordialog-class.md)
