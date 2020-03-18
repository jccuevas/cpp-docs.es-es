---
title: Clase CMFCRibbonCheckBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446233"
---
# <a name="cmfcribboncheckbox-class"></a>Clase CMFCRibbonCheckBox

La clase `CMFCRibbonCheckBox` implementa una casilla que se puede agregar a un menú emergente, a la barra de herramientas de acceso rápido o al panel de cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonCheckBox:: GetCompactSize](#getcompactsize)|(Invalida [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)).|
|[CMFCRibbonCheckBox:: GetIntermediateSize](#getintermediatesize)|(Invalida [CMFCRibbonButton:: GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)).|
|[CMFCRibbonCheckBox:: GetRegularSize](#getregularsize)|(Invalida [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)).|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Invalida `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonCheckBox:: OnDraw](#ondraw)|(Invalida [CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)).|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Invalida [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)).|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Invalida `CMFCRibbonButton::OnDrawOnList`).|
|[CMFCRibbonCheckBox:: SetACCData](#setaccdata)|(Invalida [CMFCRibbonButton:: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)).|

## <a name="remarks"></a>Observaciones

Para usar un elemento `CMFCRibbonCheckBox` en su aplicación, agregue el siguiente constructor al código:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

donde *nID* es el identificador del comando de casilla y *lpszText* es la etiqueta de texto de la casilla.

Puede Agregar una casilla a un panel de la cinta de [Opciones mediante CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncheckbox. h

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Constructor de un objeto de casilla de la cinta de opciones

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de Especifica el identificador del comando.

*lpszText*<br/>
de Especifica la etiqueta de texto.

### <a name="return-value"></a>Valor devuelto

Construye un objeto de casilla de la cinta de opciones.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCRibbonCheckBox`.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox:: GetCompactSize

Cuando se reemplaza, obtiene el tamaño compacto de la casilla.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero al CDC asociado a la casilla.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto `CSize` que contiene el tamaño compacto de la casilla.

### <a name="remarks"></a>Observaciones

Si no se reemplaza, devuelve el tamaño intermedio de la casilla.

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox:: GetIntermediateSize

Obtiene el tamaño intermedio de la casilla.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero al CDC asociado a esta casilla.

### <a name="return-value"></a>Valor devuelto

`CSize` objeto que contiene el tamaño intermedio de la casilla.

### <a name="remarks"></a>Observaciones

Si no se reemplaza, calcula el tamaño intermedio como el tamaño de la casilla de verificación predeterminada (`AFX_CHECK_BOX_DEFAULT_SIZE`) más el tamaño del texto, además de los márgenes.

##  <a name="getregularsize"></a>CMFCRibbonCheckBox:: GetRegularSize

Obtiene el tamaño normal de la casilla.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero al objeto CDC asociado a esta casilla.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto `CSize` que contiene el tamaño normal de la casilla.

### <a name="remarks"></a>Observaciones

Si no se reemplaza, devuelve el tamaño intermedio de la casilla.

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Indica si hay una imagen de información sobre herramientas asociada a la casilla.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si hay una imagen de información sobre herramientas asociada a la casilla, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

##  <a name="ondraw"></a>CMFCRibbonCheckBox:: OnDraw

Lo llama el marco de trabajo para dibujar la casilla mediante un contexto de dispositivo especificado.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero al CDC en el que se va a dibujar la casilla.

### <a name="remarks"></a>Observaciones

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Lo llama el marco de trabajo para dibujar una imagen de menú para la casilla.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parámetros

de *CDC&#42;*<br/>
Puntero al CDC asociado a la casilla.

*CRect*<br/>
de Objeto `CRect` que especifica el rectángulo en el que se va a dibujar la imagen de menú.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se dibujó la imagen, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Si no se reemplaza, devuelve FALSE.

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Lo llama el marco de trabajo para dibujar la casilla en un cuadro de lista de comandos.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero en el contexto del dispositivo en el que se va a dibujar la casilla.

*strText*<br/>
[in] El texto que se va a mostrar.

*nTextOffset*<br/>
de Distancia, en píxeles, desde el lado izquierdo del cuadro de lista hasta el texto para mostrar.

*Rect*<br/>
de Rectángulo para mostrar de la casilla.

*bIsSelected*<br/>
de TRUE si la casilla está activada, o FALSE en caso contrario.

*bHighlighted*<br/>
de TRUE si la casilla está resaltada, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

##  <a name="setaccdata"></a>CMFCRibbonCheckBox:: SetACCData

Establece los datos de accesibilidad de la casilla.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Ventana primaria de la casilla.

*data*<br/>
Los datos de accesibilidad de la casilla.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método establece los datos de accesibilidad de la casilla y siempre devuelve TRUE. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel (clase)](../../mfc/reference/cmfcribbonpanel-class.md)
