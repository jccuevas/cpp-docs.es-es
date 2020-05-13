---
title: CMFCRibbonCheckBox (clase)
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
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375251"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox (clase)

La clase `CMFCRibbonCheckBox` implementa una casilla que se puede agregar a un menú emergente, a la barra de herramientas de acceso rápido o al panel de cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Reemplaza [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Reemplaza [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Reemplaza [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Invalida `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Reemplaza [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Reemplaza [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Invalida `CMFCRibbonButton::OnDrawOnList`).|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Reemplaza [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Observaciones

Para usar un elemento `CMFCRibbonCheckBox` en su aplicación, agregue el siguiente constructor al código:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

donde *nID* es el identificador de comando de casilla de verificación y *lpszText* es la etiqueta de texto de la casilla de verificación.

Puede agregar una casilla de verificación a un panel de la cinta de opciones mediante [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Constructor de un objeto de casilla de verificación de cinta de opciones

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] Especifica el identificador de comando.

*lpszText*<br/>
[en] Especifica la etiqueta de texto.

### <a name="return-value"></a>Valor devuelto

Construye un objeto de casilla de verificación de la cinta de opciones.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonCheckBox` cómo construir un objeto de la clase.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Cuando se invalida, obtiene el tamaño compacto de la casilla de verificación.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al CDC asociado a la casilla de verificación.

### <a name="return-value"></a>Valor devuelto

Devuelve `CSize` un objeto que contiene el tamaño compacto de la casilla de verificación.

### <a name="remarks"></a>Observaciones

Si no se invalida, devuelve el tamaño intermedio de la casilla de verificación.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Obtiene el tamaño intermedio de la casilla de verificación.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al CDC asociado a esta casilla de verificación.

### <a name="return-value"></a>Valor devuelto

Objeto `CSize` que contiene el tamaño intermedio de la casilla de verificación.

### <a name="remarks"></a>Observaciones

Si no se invalida, calcula el tamaño intermedio `AFX_CHECK_BOX_DEFAULT_SIZE`como el tamaño predeterminado de la casilla de verificación ( ) más el tamaño del texto, más los márgenes.

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Obtiene el tamaño normal de la casilla de verificación.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al objeto CDC asociado a esta casilla de verificación.

### <a name="return-value"></a>Valor devuelto

Devuelve `CSize` un objeto que contiene el tamaño normal de la casilla de verificación.

### <a name="remarks"></a>Observaciones

Si no se invalida, devuelve el tamaño intermedio de la casilla de verificación.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Indica si hay una imagen de información sobre herramientas asociada a la casilla de verificación.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si hay una imagen de información sobre herramientas asociada a la casilla de verificación, o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw

Llamado por el marco de trabajo para dibujar la casilla de verificación mediante un contexto de dispositivo especificado.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al CDC en el que se va a dibujar la casilla de verificación.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Llamado por el marco de trabajo para dibujar una imagen de menú para la casilla de verificación.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parámetros

[en] *CDC&#42;*<br/>
Puntero al CDC asociado a la casilla de verificación.

*CRect*<br/>
[en] Objeto `CRect` que especifica el rectángulo en el que se va a dibujar la imagen del menú.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha dibujado la imagen o FALSE si no.

### <a name="remarks"></a>Observaciones

Si no se invalida, devuelve FALSE.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Llamado por el marco de trabajo para dibujar la casilla de verificación en un cuadro de lista de comandos.

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
[en] Puntero al contexto del dispositivo en el que se va a dibujar la casilla de verificación.

*strText*<br/>
[in] El texto que se va a mostrar.

*nTextOffset*<br/>
[en] La distancia, en píxeles, desde el lado izquierdo del cuadro de lista hasta el texto de visualización.

*Rect*<br/>
[en] El rectángulo de visualización de la casilla de verificación.

*bIsSelected*<br/>
[en] TRUESi la casilla de verificación está activada, o FALSE si no.

*bResaltado*<br/>
[en] TRUESi la casilla de verificación está resaltada, o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Establece los datos de accesibilidad de la casilla de verificación.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
La ventana principal de la casilla de verificación.

*datos*<br/>
Los datos de accesibilidad de la casilla de verificación.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método establece los datos de accesibilidad de la casilla de verificación y siempre devuelve TRUE. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel Clase](../../mfc/reference/cmfcribbonpanel-class.md)
