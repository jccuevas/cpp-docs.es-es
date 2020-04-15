---
title: CMFCRibbonSlider Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: f2a05ca1433ca3a44b0459360e3f09fe7a274c68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368829"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider Clase

La `CMFCRibbonSlider` clase implementa un control deslizante que puede agregar a una barra de la cinta de opciones o a una barra de estado de la cinta de opciones. El control deslizante de la cinta es similar a los controles deslizantes del zoom que aparecen en las aplicaciones de Office 2007.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Construye e inicializa un control deslizante de la cinta de opciones.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Devuelve la posición actual del control deslizante.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Devuelve el valor máximo del control deslizante.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del control deslizante.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Reemplaza [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Devuelve el tamaño del incremento de zoom para el control deslizante.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Especifica si el control deslizante tiene botones de zoom.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Reemplaza [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Establece la posición actual del control deslizante.|
|[CMFCRibbonSlider::SetRange](#setrange)|Especifica el intervalo del control deslizante estableciendo los valores mínimo y máximo.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Muestra u oculta los botones de zoom.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Establece el tamaño del incremento de zoom para el control deslizante.|

## <a name="remarks"></a>Observaciones

Puede utilizar `SetRange` el método para configurar el rango de incrementos de zoom para el control deslizante. Puede establecer la posición actual del `SetPos` control deslizante mediante el método.

Puede mostrar botones de zoom circular en el lado `SetZoomButtons` izquierdo y derecho del control deslizante mediante el método. De forma predeterminada, el control deslizante es horizontal, el botón de zoom izquierdo muestra un signo menos y el botón de zoom derecho muestra un signo más.

El `SetZoomIncrement` método define el incremento que se va a agregar o restar de la posición actual cuando un usuario hace clic en los botones de zoom.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonSlider` cómo utilizar varios métodos de la clase para establecer las propiedades del control deslizante. En el ejemplo se `CMFCRibbonSlider` muestra cómo construir un objeto, mostrar botones de zoom, establecer la posición actual del control deslizante y establecer el rango de valores para el control deslizante.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonslider.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider

Construir un control deslizante de la cinta de opciones.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] ID del deslizador.

[in]. *nAncho* Ancho del control deslizante en píxeles.

### <a name="remarks"></a>Observaciones

Construye un control deslizante de la cinta de opciones que tiene *nWidth* píxeles de ancho en la categoría de panel donde se agrega el control deslizante. De forma predeterminada, el control deslizante es horizontal.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFCRibbonSlider::GetPos

Devuelve la posición actual del control deslizante.

```
int GetPos() const;
```

### <a name="return-value"></a>Valor devuelto

La posición actual del control deslizante, que es una posición relativa al principio del control deslizante.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax

Obtiene el incremento máximo del control deslizante que el control deslizante puede recorrer en el control deslizante.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento máximo del control deslizante que el control deslizante puede recorrer en el control deslizante.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin

Devuelve el incremento mínimo que el control deslizante puede recorrer en el control deslizante.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento mínimo que el control deslizante puede recorrer en el control deslizante.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement

Obtenga el incremento de zoom para el control deslizante.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento de zoom para el control deslizante.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons

Especifica si el control deslizante tiene botones de zoom.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el control deslizante tiene botones de zoom; FALSE en caso contrario.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFCRibbonSlider::OnDraw

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFCRibbonSlider::SetPos

Establezca la posición actual del control deslizante.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
[en] Especifica la posición que se establecerá para el control deslizante. La posición es relativa al principio del control deslizante.

*bRedraw*<br/>
[en] Si es TRUE, se volverá a dibujar el control deslizante.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFCRibbonSlider::SetRange

Establezca el rango de valores para el control deslizante.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
[en] Especifica el valor mínimo del control deslizante.

*nMax*<br/>
[en] Especifica el valor máximo del control deslizante.

### <a name="remarks"></a>Observaciones

Especifica el intervalo de valores para el control deslizante estableciendo los valores mínimo y máximo.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons

Mostrar u ocultar botones de zoom.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parámetros

[in]. *bSet* TRUE para mostrar los botones de zoom; FALSE para ocultarlos.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement

Establezca el incremento de zoom para el control deslizante.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parámetros

*nZoomIncrement*<br/>
[en] Especifica el incremento de zoom del control deslizante.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement Clase](../../mfc/reference/cmfcribbonbaseelement-class.md)
