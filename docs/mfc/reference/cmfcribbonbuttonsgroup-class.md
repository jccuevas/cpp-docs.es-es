---
title: CMFCRibbonButtonsGroup (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: af5919ff2a72fc2aa1eeeb95fc93afbe9e743582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375284"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup (clase)

La `CMFCRibbonButtonsGroup` clase le permite organizar un conjunto de botones de la cinta de opciones en un grupo. Todos los botones del grupo son directamente adyacentes a otros horizontalmente y se incluyen en un borde.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Construye un objeto `CMFCRibbonButtonsGroup`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Agrega un botón a un grupo.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Agrega una lista de botones a un grupo.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Devuelve un puntero al botón que se encuentra en un índice especificado.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Devuelve el número de botones del grupo.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Devuelve el tamaño de imagen de las imágenes normales en el grupo de la cinta de opciones (reemplaza [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta de opciones (reemplaza [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Indica si `CMFCRibbonButtonsGroup` el objeto contiene imágenes de la barra de herramientas.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dibuja la imagen adecuada para un botón especificado, dependiendo de si el botón es normal, resaltado o deshabilitado.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Quita todos los `CMFCRibbonButtonsGroup` botones del objeto.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Asigna imágenes al grupo.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Establece el `CMFCRibbonCategory` elemento `CMFCRibbonButtonsGroup` primario del objeto y todos los botones dentro de él (reemplaza [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Observaciones

El grupo se deriva de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) y se puede manipular como una sola entidad. Puede colocar el grupo en cualquier panel o menú emergente.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonButtonsGroup` . En el ejemplo se `CMFCRibbonButtonsGroup` muestra cómo construir un objeto, asignar imágenes al grupo de botones de la cinta de opciones y agregar un botón al grupo de botones de la cinta de opciones. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonbuttonsgroup.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton

Agrega un botón a un grupo.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[en] Un puntero a un botón para agregar.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons

Agrega una lista de botones a un grupo.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parámetros

*lstButtons*<br/>
[en] Una lista de punteros a los botones que desea agregar.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Construye un objeto `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[en] Especifica un botón para agregar `CMFCRibbonButtonsGroup` al objeto recién creado.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton

Devuelve un puntero al botón que se encuentra en un índice especificado.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
[en] Un índice de base cero de un botón que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Puntero al botón que se encuentra en el índice especificado. NULL si el índice especificado está fuera del intervalo.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount

Devuelve el número de botones del grupo.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de botones del grupo.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize

Recupera el tamaño de la `CMFCToolBarImages` `m_Images`imagen de origen del miembro protegido.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño de la imagen de origen de `CSize` las imágenes de la barra de herramientas, si hay alguna, o un de cero si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize

Recupera el tamaño máximo posible del elemento de grupo de cinta de opciones.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al contexto de dispositivo del grupo de cinta de opciones.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages

Indica si `CMFCRibbonButtonsGroup` el objeto contiene imágenes de la barra de herramientas.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si `CMFCToolBarImages` `m_Images` el miembro protegido contiene imágenes o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage

Dibuja la imagen adecuada para un botón especificado, dependiendo de si el botón es normal, resaltado o deshabilitado.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al contexto del `CMFCRibbonButtonsGroup` dispositivo del objeto.

*rectImage*<br/>
[en] El rectángulo dentro del cual se va a dibujar la imagen.

*pButton*<br/>
[en] El botón para el que desea dibujar la imagen.

*nImageIndex*<br/>
[en] El índice de la imagen que se va a dibujar en el botón (en una de las tres matrices de imágenes para los botones normales, resaltados o deshabilitados).

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll

Quita todos los `CMFCRibbonButtonsGroup` botones del objeto.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages

Asigna imágenes al grupo de botones de la cinta de opciones.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parámetros

*pImages*<br/>
[en] Imágenes regulares.

*pHotImages*<br/>
[en] Imágenes calientes.

*pDisabledImages*<br/>
[en] Imágenes desactivadas.

### <a name="remarks"></a>Observaciones

Llame `SetImages` antes de agregar botones a un grupo. El número de imágenes debe ser mayor o igual que el número de botones que se agregarán al grupo.

> [!NOTE]
> Las imágenes en caliente son imágenes que se muestran cuando el usuario pasa el cursor sobre el botón. Las imágenes desactivadas son imágenes que se muestran cuando el botón está deshabilitado.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory

Establece el `CMFCRibbonCategory` elemento `CMFCRibbonButtonsGroup` primario del objeto y todos los botones dentro de él.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parámetros

*pCategory*<br/>
[en] Puntero a la categoría primaria que se va a establecer (los grupos con fichas de los controles de la cinta de opciones se denominan categorías).

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
