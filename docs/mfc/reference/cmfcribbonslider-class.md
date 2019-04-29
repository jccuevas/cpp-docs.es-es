---
title: CMFCRibbonSlider (clase)
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
ms.openlocfilehash: 85c646e2fa524268e4559b587f90c5e06971b765
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374082"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider (clase)

La `CMFCRibbonSlider` clase implementa un control deslizante que se puede agregar a una barra de cinta de opciones o la barra de estado de la cinta de opciones. El control deslizante de la cinta es similar a los controles deslizantes del zoom que aparecen en las aplicaciones de Office 2007.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Crea e inicializa un control deslizante de cinta de opciones.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Devuelve la posición actual del control deslizante.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Devuelve el valor máximo del control deslizante.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del control deslizante.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Devuelve el tamaño del incremento de zoom para el control deslizante.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Especifica si el control deslizante tiene botones de zoom.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [cmfcribbonbaseelement:: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Establece la posición actual del control deslizante.|
|[CMFCRibbonSlider::SetRange](#setrange)|Especifica el intervalo del control deslizante estableciendo los valores mínimos y máximo.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Muestra u oculta los botones de zoom.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Establece el tamaño del incremento de zoom para el control deslizante.|

## <a name="remarks"></a>Comentarios

Puede usar el `SetRange` método para configurar el intervalo de incrementos de zoom para el control deslizante. Puede establecer la posición actual del control deslizante mediante el `SetPos` método.

Puede mostrar botones de zoom circular a la izquierda y derecha del control deslizante mediante el `SetZoomButtons` método. De forma predeterminada, el control deslizante es horizontal, el botón de zoom izquierdo muestra un signo menos y el botón de zoom derecho muestra un signo más.

El `SetZoomIncrement` método define el incremento para agregar o restar desde la posición actual cuando un usuario hace clic en los botones de zoom.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCRibbonSlider` clase para establecer las propiedades del control deslizante. En el ejemplo se muestra cómo construir un `CMFCRibbonSlider` objeto, mostrar botones de zoom, establecer la posición actual del control deslizante y establezca el intervalo de valores para el control deslizante.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonslider.h

##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider

Crear un control deslizante de la cinta de opciones.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[in] Id. de control deslizante.

[in]. *nWidth* ancho del control deslizante en píxeles.

### <a name="remarks"></a>Comentarios

Construye un control deslizante de la cinta de opciones que es *nWidth* píxeles de ancho de la categoría de panel que se agrega el control deslizante. De forma predeterminada, el control deslizante es horizontal.

##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos

Devuelve la posición actual del control deslizante.

```
int GetPos() const;
```

### <a name="return-value"></a>Valor devuelto

La posición actual del control deslizante, que es una posición en relación con el principio del control deslizante.

##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax

Obtiene el incremento máximo del control deslizante que el control deslizante puede viajar en el control deslizante.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento máximo del control deslizante que el control deslizante puede viajar en el control deslizante.

##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin

Devuelve el incremento mínimo que el control deslizante puede viajar en el control deslizante.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento mínimo que el control deslizante puede viajar en el control deslizante.

##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[in] *pDC*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement

Obtener el incremento de zoom para el control deslizante.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento de zoom para el control deslizante.

##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons

Especifica si el control deslizante tiene botones de zoom.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control deslizante tiene botones de zoom; FALSE en caso contrario.

##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[in] *pDC*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos

Establezca la posición actual del control deslizante.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
[in] Especifica la posición para establecer para el control deslizante. La posición es relativa al principio del control deslizante.

*bRedraw*<br/>
[in] Si es TRUE, se volverá a dibujar el control deslizante.

##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange

Establezca el intervalo de valores para el control deslizante.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
[in] Especifica el valor mínimo del control deslizante.

*nMax*<br/>
[in] Especifica el valor máximo del control deslizante.

### <a name="remarks"></a>Comentarios

Especifica el intervalo de valores para el control deslizante estableciendo los valores mínimos y máximo.

##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons

Mostrar u ocultar los botones de zoom.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parámetros

[in]. *bSet* True para mostrar los botones de zoom; FALSE para ocultarlas.

##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement

Establecer el incremento de zoom para el control deslizante.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parámetros

*nZoomIncrement*<br/>
[in] Especifica el incremento de zoom del control deslizante.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement (clase)](../../mfc/reference/cmfcribbonbaseelement-class.md)
