---
title: CMFCToolBarFontSizeComboBox (Clase)
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
ms.openlocfilehash: 09811b14ed805b1965015a32a25c0b67c947ff4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358307"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox (Clase)

Un botón de barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar un tamaño de fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Construye un objeto `CMFCToolBarFontSizeComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Devuelve el tamaño de fuente seleccionado en twips.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Rellena la lista de cuadros combinados con todos los tamaños de fuente admitidos para una fuente especificada.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Establece el tamaño de fuente en twips.|

## <a name="remarks"></a>Observaciones

Puede utilizar `CMFCToolBarFontSizeComboBox` un objeto junto con un [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objeto para permitir a un usuario seleccionar una fuente y el tamaño de fuente.

Puede agregar un botón de cuadro combinado de tamaño de fuente a una barra de herramientas del igual que agrega un botón de cuadro combinado de fuente. Para obtener más información, vea [CMFCToolBarFontComboBox (Clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Cuando el usuario selecciona una `CMFCToolBarFontComboBox` nueva fuente en un objeto, puede rellenar el cuadro combinado de tamaño de fuente con los tamaños admitidos para esa fuente mediante el [método CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCToolBarFontSizeComboBox` cómo utilizar `CMFCToolBarFontSizeComboBox` varios métodos en la clase para configurar un objeto. En el ejemplo se muestra cómo recuperar el tamaño de fuente, en twips, del cuadro de texto, rellenar el cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente dada y especificar el tamaño de fuente en twips. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Construye un objeto `CMFCToolBarFontSizeComboBox`.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize

Recupera el tamaño de fuente, en twips, del cuadro de texto de un cuadro combinado de tamaño de fuente.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es positivo, es el tamaño de fuente en twips. Es -1 si el cuadro de texto del cuadro combinado está vacío. Es -2 si se produce un error.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes

Rellena un cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente dada.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parámetros

*strFontName*<br/>
[en] Especifica un nombre de fuente.

### <a name="remarks"></a>Observaciones

Llame a esta función cuando desee sincronizar entre la selección en un cuadro combinado de fuente y un cuadro combinado de tamaño de fuente, como una [clase CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize

Redondea el tamaño especificado (en twips) al tamaño más cercano en puntos y, a continuación, establece el tamaño seleccionado en el cuadro combinado en ese valor.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
[en] Especifica el tamaño de fuente (en twips) que se va a establecer.

### <a name="remarks"></a>Observaciones

Puede recuperar el tamaño de fuente válido anterior más adelante mediante una llamada a la [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) método.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (Clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo (Clase)](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
