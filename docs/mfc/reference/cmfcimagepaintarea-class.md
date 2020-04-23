---
title: CMFCImagePaintArea (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: cd74d2418bb874553fbbafa637f527a7b84b73bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754271"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea (Clase)

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

### <a name="remarks"></a>Observaciones

Esta clase no está pensada para utilizarla directamente desde el código.

El marco de trabajo utiliza esta clase para mostrar el área de imagen en un cuadro de diálogo del editor de imágenes. Para obtener más información sobre el cuadro de diálogo del editor de imágenes, vea [CMFCImageEditorDialog (Clase)](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCImagePaintArea` cómo construir un objeto de la clase, establecer el color de dibujo actual, establecer el modo de dibujo actual y establecer la imagen de mapa de bits para el área de imagen.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afximagepaintarea.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea

Construye un objeto `CMFCImagePaintArea`.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pParentDlg*|[en] Puntero al cuadro de diálogo que es el elemento primario del editor de imágenes.|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFCImagePaintArea::GetMode

Recupera el modo de dibujo actual.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Valor devuelto

Un [valor IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) que especifica el modo de dibujo actual.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap

Establece la imagen de mapa de bits para el área de imagen.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pBitmap*|[en] La nueva imagen de mapa de bits que se va a mostrar.|

### <a name="remarks"></a>Observaciones

Si *pBitmap* es NULL, este método establece el tamaño del área de pintura modificable en cero. De lo contrario, establece el tamaño del área de pintura modificable en el tamaño de la imagen de mapa de bits proporcionada.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFCImagePaintArea::SetColor

Establece el color de dibujo actual.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*color*|[en] El nuevo color de dibujo.|

### <a name="remarks"></a>Observaciones

Al seleccionar un color en la barra de paletas del editor de imágenes o en el selector de color, el marco de trabajo llama a este método para actualizar el color de dibujo actual. El color de dibujo inicial es negro (un valor COLORREF de 0).

El cuadro de diálogo del editor de imágenes utiliza el color de dibujo para todos los modos de dibujo, excepto para IMAGE_EDIT_MODE_COLOR. Para obtener más información acerca de los modos de dibujo, vea [CMFCImagePaintArea::IMAGE_EDIT_MODE (Enumeración).](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFCImagePaintArea::SetMode

Establece el modo de dibujo actual.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*Modo*|[en] Un [valor IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) que especifica el modo de dibujo actual.|

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog (Clase)](../../mfc/reference/cmfcimageeditordialog-class.md)
