---
title: CMFCRibbonUndoButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: f30e6f78b0988b791617ee0926cf649377972ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368813"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton (clase)

La `CMFCRibbonUndoButton` clase implementa un botón de lista desplegable que contiene los comandos de usuario más recientes. Los usuarios pueden seleccionar uno o varios de los comandos más recientes de la lista desplegable para rehacerlos o deshacerlos.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construye un `CMFCRibbonUndoButton` nuevo objeto mediante el identificador de comando que especifique, la etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Agrega una nueva acción a la lista de acciones.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Borra la lista de acciones, que es la lista desplegable.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Determina el número de elementos que un usuario seleccionó en la lista desplegable.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indica si el objeto contiene un menú.|

## <a name="remarks"></a>Observaciones

La `CMFCRibbonUndoButton` clase utiliza una pila para representar la lista desplegable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonUndoButton` cómo construir un objeto de la clase y agregar una nueva acción a la lista de acciones. Este fragmento de código forma parte del [ejemplo Deretos](../../overview/visual-cpp-samples.md)de la cinta de opciones.

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction

Agrega una nueva acción a la lista de acciones.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] La etiqueta de acción que se mostrará en la lista desplegable.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList

Borra la lista de acciones, que es la lista desplegable.

```
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton

Construye un `CMFCRibbonUndoButton` nuevo objeto mediante el identificador de comando que especifique, la etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] Especifica el identificador de comando.

*lpszText*<br/>
[en] Especifica la etiqueta de texto del botón.

*nSmallImageIndex*<br/>
[en] El índice de base cero en la lista de imágenes del objeto primario para la imagen pequeña del botón.

*nLargeImageIndex*<br/>
[en] El índice de base cero en la lista de imágenes del objeto primario para la imagen grande del botón.

*hIcon*<br/>
[en] Identificador de un icono que puede usar como imagen de un botón.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber

Determina el número de elementos que un usuario seleccionó en la lista desplegable.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que ha seleccionado un usuario.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu

Indica si el objeto contiene un menú.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery (Clase)](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
