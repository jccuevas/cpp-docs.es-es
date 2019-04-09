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
ms.openlocfilehash: 39979d48eb7b0f7aba9dbe7bd42c2f91845af968
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781996"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup (clase)

La `CMFCRibbonButtonsGroup` clase le permite organizar un conjunto de botones de cinta de opciones en un grupo. Todos los botones del grupo son directamente adyacentes a otros horizontalmente y se incluyen en un borde.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Construye un objeto `CMFCRibbonButtonsGroup`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Agrega un botón a un grupo.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Agrega una lista de botones a un grupo.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Devuelve un puntero al botón que se encuentra en el índice especificado.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Devuelve el número de botones en el grupo.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Devuelve el tamaño de la imagen de las imágenes normales en el grupo de la cinta de opciones (invalidaciones [cmfcribbonbaseelement:: Getimagesize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento cinta (invalidaciones [cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Los informes si el `CMFCRibbonButtonsGroup` objeto contiene imágenes de barra de herramientas.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dibuja la imagen adecuada para un botón especificado, dependiendo de si el botón es normal, resaltada o deshabilitado.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Quita todos los botones de la `CMFCRibbonButtonsGroup` objeto.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Las imágenes se asigna al grupo.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Establece el elemento primario `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objeto y todos los botones dentro de él (invalidaciones [cmfcribbonbaseelement:: Setparentcategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Comentarios

El grupo se deriva [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) y se puede manipular como una sola entidad. El grupo se puede colocar en cualquier panel o un menú emergente.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonButtonsGroup` . En el ejemplo se muestra cómo construir un `CMFCRibbonButtonsGroup` objeto, asignar imágenes para el grupo de botones de cinta de opciones y agregar un botón al grupo de botones de la cinta. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonbuttonsgroup.h

##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton

Agrega un botón a un grupo.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[in] Un puntero a un botón para agregar.

##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons

Agrega una lista de botones a un grupo.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parámetros

*lstButtons*<br/>
[in] Una lista de punteros a los botones que desea agregar.

##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Construye un objeto `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[in] Especifica un botón para agregar recién creado `CMFCRibbonButtonsGroup` objeto.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton

Devuelve un puntero al botón que se encuentra en el índice especificado.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parámetros

*i*<br/>
[in] Índice de base cero de un botón para devolver.

### <a name="return-value"></a>Valor devuelto

Un puntero al botón que se encuentra en el índice especificado. Es NULL si el índice especificado está fuera del intervalo.

### <a name="remarks"></a>Comentarios

##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount

Devuelve el número de botones en el grupo.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de botones en el grupo.

##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize

Recupera el tamaño de la imagen de origen del elemento protegido `CMFCToolBarImages` miembro `m_Images`.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño de la imagen de origen de las imágenes de la barra de herramientas, si hubiera alguno, o un `CSize` de cero si no lo es.

### <a name="remarks"></a>Comentarios

##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize

Recupera el tamaño máximo posible del elemento de grupo de cinta de opciones.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero al contexto de dispositivo del grupo de cinta de opciones.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages

Los informes si el `CMFCRibbonButtonsGroup` objeto contiene imágenes de barra de herramientas.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el modo protegido `CMFCToolBarImages` miembro `m_Images` contiene las imágenes, o FALSE si no.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage

Dibuja la imagen adecuada para un botón especificado, dependiendo de si el botón es normal, resaltada o deshabilitado.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero al contexto de dispositivo de la `CMFCRibbonButtonsGroup` objeto.

*rectImage*<br/>
[in] El rectángulo dentro del cual se va a dibujar la imagen.

*pButton*<br/>
[in] El botón para que se va a dibujar la imagen.

*nImageIndex*<br/>
[in] El índice de la imagen para dibujar en el botón (en una de las matrices de tres imágenes para los botones normales, resaltadas o deshabilitados).

### <a name="remarks"></a>Comentarios

##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll

Quita todos los botones de la `CMFCRibbonButtonsGroup` objeto.

```
void RemoveAll();
```

### <a name="remarks"></a>Comentarios

##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages

Las imágenes se asigna al grupo de botones de la cinta.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parámetros

*pImages*<br/>
[in] Imágenes normales.

*pHotImages*<br/>
[in] Imágenes activas.

*pDisabledImages*<br/>
[in] Imágenes deshabilitadas.

### <a name="remarks"></a>Comentarios

Llame a `SetImages` antes de agregar botones a un grupo. El número de imágenes debe ser mayor o igual que el número de botones que deben agregarse al grupo.

> [!NOTE]
>  Acceso rápido son imágenes que se muestran cuando el usuario mantiene el puntero sobre el botón. Deshabilitado son imágenes que se muestran cuando el botón está deshabilitado.

##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory

Establece el elemento primario `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objeto y todos los botones dentro de él.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parámetros

*pCategory*<br/>
[in] Puntero a la categoría primaria para establecer (los grupos con pestañas en los controles de cinta de opciones se denominan categorías).

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
