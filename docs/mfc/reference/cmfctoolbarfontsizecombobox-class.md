---
title: CMFCToolBarFontSizeComboBox (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: a1dd85ed7bf80f5307bf0bd07ef5ef74875c8562
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258949"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox (clase)

Un botón de barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar un tamaño de fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Construye un objeto `CMFCToolBarFontSizeComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Devuelve el tamaño de fuente seleccionada en twips.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|La lista del cuadro combinado se rellena con todos los tamaños de fuente admitido para una fuente determinada.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Establece el tamaño de fuente en twips.|

## <a name="remarks"></a>Comentarios

Puede usar un `CMFCToolBarFontSizeComboBox` objeto junto con un [CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objeto para permitir al usuario seleccionar una fuente y tamaño.

Puede agregar un botón de cuadro combinado de tamaño de fuente a una barra de herramientas, tal como agregar un botón de cuadro combinado de fuente. Para obtener más información, consulte [CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Cuando el usuario selecciona una nueva fuente en un `CMFCToolBarFontComboBox` objeto, puede rellenar el cuadro combinado de tamaño de fuente con los tamaños admitidos para esa fuente utilizando el [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) método.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCToolBarFontSizeComboBox` clase para configurar un `CMFCToolBarFontSizeComboBox` objeto. El ejemplo muestra cómo recuperar el tamaño de fuente, en twips, desde el cuadro de texto, rellene el cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente determinada y especificar el tamaño de fuente en twips. Este fragmento de código forma parte del [ejemplo de WordPad](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Construye un objeto `CMFCToolBarFontSizeComboBox`.

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

Recupera el tamaño de fuente, en twips, desde el cuadro de texto de un cuadro combinado de tamaño de fuente.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es positivo, es el tamaño de fuente en twips. Es -1 si el cuadro de texto del cuadro combinado está vacío. Es -2 si se produce un error.

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

Un cuadro combinado de tamaño de fuente se rellena con todos los tamaños válidos de la fuente determinada.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parámetros

*strFontName*<br/>
[in] Especifica un nombre de fuente.

### <a name="remarks"></a>Comentarios

Llame a esta función cuando desee sincronizar entre la selección de un cuadro combinado de fuente y un cuadro combinado de tamaño de fuente, como un [CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

Redondea especificado tamaño (en twips) para el tamaño más cercano en puntos y, a continuación, Establece el tamaño seleccionado en el cuadro combinado para ese valor.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
[in] Especifica el tamaño de fuente (en twips) para establecer.

### <a name="remarks"></a>Comentarios

Puede recuperar el tamaño de fuente válida anterior más adelante mediante una llamada a la [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) método.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Insertar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
