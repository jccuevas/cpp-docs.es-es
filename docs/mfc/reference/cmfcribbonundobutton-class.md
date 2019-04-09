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
ms.openlocfilehash: cd657ac035c004e7aa9bfcd2f6dbd2f3c90da80c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776471"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton (clase)

La `CMFCRibbonUndoButton` clase implementa un botón de lista desplegable que contiene los comandos más recientes del usuario. Los usuarios pueden seleccionar uno o varios de los comandos más recientes en la lista desplegable para rehacer o deshacer.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construye un nuevo `CMFCRibbonUndoButton` objeto con el identificador de comando que especifique, etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Agrega una nueva acción a la lista de acciones.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Borra la lista de acciones, que es la lista desplegable.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Determina el número de elementos que el usuario seleccionado en la lista desplegable.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indica si el objeto contiene un menú.|

## <a name="remarks"></a>Comentarios

La `CMFCRibbonUndoButton` clase utiliza una pila para representar la lista desplegable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonUndoButton` de clases y agregue una nueva acción a la lista de acciones. Este fragmento de código forma parte de la [ejemplo Gadgets de la cinta de opciones](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

Agrega una nueva acción a la lista de acciones.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] La etiqueta de acción que se mostrará en la lista desplegable.

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

Borra la lista de acciones, que es la lista desplegable.

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

Construye un nuevo `CMFCRibbonUndoButton` objeto con el identificador de comando que especifique, etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.

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
[in] Especifica el identificador de comando.

*lpszText*<br/>
[in] Especifica la etiqueta de texto del botón.

*nSmallImageIndex*<br/>
[in] Índice de base cero en la lista de imágenes del objeto primario para la imagen del botón pequeño.

*nLargeImageIndex*<br/>
[in] Índice de base cero en la lista de imágenes del objeto primario para el de la imagen grande del botón.

*hIcon*<br/>
[in] Identificador de un icono que se puede usar como imagen de un botón.

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

Determina el número de elementos que el usuario seleccionado en la lista desplegable.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que el usuario seleccionado.

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

Indica si el objeto contiene un menú.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery (clase)](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
