---
title: CMFCImageEditorDialog (clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 57b1df49616967841a433a36a504beed0b900cde
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278540"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog (clase)

La `CMFCImageEditorDialog` clase es compatible con un cuadro de diálogo del editor de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Construye un objeto `CMFCImageEditorDialog`.|

## <a name="remarks"></a>Comentarios

La `CMFCImageEditorDialog` clase proporciona un cuadro de diálogo que incluye:

- Un área de imagen que se utiliza para modificar los píxeles individuales de una imagen.

- Herramientas para modificar los píxeles en el área de dibujo.

- Una paleta de colores para especificar el color que se utiliza por las herramientas de dibujo.

- Un área de vista previa que muestra el efecto de la edición.

La siguiente ilustración muestra a un editor de imágenes de cuadro de diálogo.

![Cuadro de diálogo CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "cuadro de diálogo CMFCImageEditorDialog")

Una forma de usar un `CMFCImageEditorDialog` objeto es pasarlo un `CBitmap` imagen que se va a editar. No cree una imagen grande porque el área de edición de imágenes tiene un tamaño limitado y el tamaño de píxel lógico se ajusta para adaptarse al área. Llame a la `DoModal` método para iniciar un cuadro de diálogo modal.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

Construye un objeto `CMFCImageEditorDialog`.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
Puntero a una imagen.

*pParent*<br/>
Puntero a la ventana primaria del cuadro de diálogo de editor de imagen actual.

*nBitsPixel*<br/>
El número de bits que se usa para representar el color de un solo píxel, que también se conoce como la profundidad de color.  Si el *nBitsPixel* parámetro es -1, la profundidad de color se deriva de la imagen especificada por el *pBitmap* parámetro. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

Para modificar una imagen, pasar un puntero de la imagen a la `CMFCImageEditorDialog` constructor. A continuación, llame a la `DoModal` método para abrir el cuadro de diálogo modal. Cuando el `DoModal` método vuelve, contiene la nueva imagen.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCImageEditorDialog` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
