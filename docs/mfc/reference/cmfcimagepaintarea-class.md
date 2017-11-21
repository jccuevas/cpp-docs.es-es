---
title: Clase CMFCImagePaintArea | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs: C++
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70888bbd0acaef49bac67147bff4fe7719a84404
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea (clase)
Proporciona el área de imagen que se utiliza para modificar una imagen en un cuadro de diálogo del editor de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Construye un objeto `CMFCImagePaintArea`.|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCImagePaintArea::GetMode](#getmode)|Recupera el modo de dibujo actual.|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Establece la imagen de mapa de bits para el área de imagen.|  
|[CMFCImagePaintArea::SetColor](#setcolor)|Establece el color de dibujo actual.|  
|[CMFCImagePaintArea::SetMode](#setmode)|Establece el modo de dibujo actual.|  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no está diseñada para utilizarse directamente desde el código.  
  
 El marco de trabajo utiliza esta clase para mostrar el área de imagen en un cuadro de diálogo del editor de imágenes. Para obtener más información sobre el cuadro de diálogo del editor de imágenes, vea [CMFCImageEditorDialog clase](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCImagePaintArea` de clases, establecer el actual dibujando color, establecer el modo de dibujo actual y establecer la imagen de mapa de bits para el área de imagen.  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea  
 Construye un objeto `CMFCImagePaintArea`.  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pParentDlg`|Un puntero al cuadro de diálogo que es el elemento primario del editor de imágenes.|  
  
##  <a name="getmode"></a>CMFCImagePaintArea::GetMode  
 Recupera el modo de dibujo actual.  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valor que especifica el modo de dibujo actual.  
  
##  <a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap  
 Establece la imagen de mapa de bits para el área de imagen.  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pBitmap`|La nueva imagen de mapa de bits para mostrar.|  
  
### <a name="remarks"></a>Comentarios  
 Si `pBitmap` es `NULL`, este método establece el tamaño del área de pintura modificable en cero. En caso contrario, Establece el tamaño del área de pintura modificable en el tamaño de la imagen de mapa de bits proporcionado.  
  
##  <a name="setcolor"></a>CMFCImagePaintArea::SetColor  
 Establece el color de dibujo actual.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `color`|El nuevo color de dibujo.|  
  
### <a name="remarks"></a>Comentarios  
 Cuando seleccione un color en la barra de paleta del editor de imágenes o selector de color, el marco de trabajo llama a este método para actualizar el color de dibujo actual. El color de dibujo inicial es negro (un `COLORREF` el valor 0).  
  
 Se utiliza el color de dibujo mediante el cuadro de diálogo del editor de imágenes para todos los modos de dibujo excepto `IMAGE_EDIT_MODE_COLOR`. Para obtener más información acerca de los modos de dibujo, consulte [Cmfcimagepaintarea enumeración](cmfcimagepaintarea-image-edit-mode-enumeration.md).  
  
##  <a name="setmode"></a>CMFCImagePaintArea::SetMode  
 Establece el modo de dibujo actual.  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `mode`|Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valor que especifica el modo de dibujo actual.|  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog (clase)](../../mfc/reference/cmfcimageeditordialog-class.md)
