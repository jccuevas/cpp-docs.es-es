---
title: CMFCImageEditorDialog (Clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367463"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog (Clase)

La `CMFCImageEditorDialog` clase admite un cuadro de diálogo del editor de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Construye un objeto `CMFCImageEditorDialog`.|

## <a name="remarks"></a>Observaciones

La `CMFCImageEditorDialog` clase proporciona un cuadro de diálogo que incluye:

- Un área de imagen que se utiliza para modificar píxeles individuales en una imagen.

- Herramientas de dibujo para modificar los píxeles del área de imagen.

- Una paleta de colores para especificar el color que utilizan las herramientas de dibujo.

- Un área de vista previa que muestra el efecto de la edición.

En la siguiente ilustración se muestra un cuadro de diálogo del editor de imágenes.

![Cuadro de diálogo CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "Cuadro de diálogo CMFCImageEditorDialog")

Una forma de `CMFCImageEditorDialog` utilizar un objeto `CBitmap` es pasarle una imagen que se va a editar. No cree una imagen grande porque el área de edición de imágenes tiene un tamaño limitado y el tamaño de píxel lógico se ajusta para ajustarse al área. Llame `DoModal` al método para iniciar un cuadro de diálogo modal.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afximageeditordialog.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog

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
Puntero a la ventana principal del cuadro de diálogo del editor de imágenes actual.

*nBitsPixel*<br/>
El número de bits utilizados para representar el color de un solo píxel, que también se conoce como profundidad de color.  Si el *nBitsPixel* parámetro es -1, la profundidad de color se deriva de la imagen especificada por el *pBitmap* parámetro. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

Para modificar una imagen, pase `CMFCImageEditorDialog` un puntero de imagen al constructor. A continuación, llame al `DoModal` método para abrir un cuadro de diálogo modal. Cuando `DoModal` el método devuelve, el mapa de bits contiene la nueva imagen.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCImageEditorDialog` cómo construir un objeto de la clase. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)
