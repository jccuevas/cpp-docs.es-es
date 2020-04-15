---
title: CMFCRibbonProgressBar Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: 063f8ce560af84d350abc0114644f6a63f969f95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368859"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar Clase

Implementa un control que indica visualmente el progreso de una operación larga.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Construye e inicializa un objeto `CMFCRibbonProgressBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Devuelve el progreso actual.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Devuelve el valor máximo del intervalo actual.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del intervalo actual.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Reemplaza [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Especifica si la barra de progreso funciona en modo infinito.|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Reemplaza [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Establece la barra de progreso para que funcione en modo infinito.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Establece el progreso actual.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Establece los valores mínimo y máximo.|

## <a name="remarks"></a>Observaciones

A `CMFCRibbonProgressBar` puede funcionar en dos modos: regular e infinito. En el modo normal, la barra de progreso se rellena de izquierda a derecha y se detiene cuando alcanza el valor máximo. En el modo infinito, la barra de progreso se rellena repetidamente desde el valor mínimo hasta el valor máximo. Puede usar el modo infinito para indicar que una operación está en curso, pero que el tiempo de finalización es desconocido.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonProgressBar` . En el ejemplo se muestra cómo establecer la barra de progreso para que funcione en modo infinito (donde se desconoce el tiempo de finalización de una operación), establecer los valores mínimo y máximo para la barra de progreso y establecer la posición actual de la barra de progreso. Este fragmento de código forma parte del ejemplo de demostración de [MS Office 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar

Construye e inicializa un [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objeto.

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] Especifica el identificador de comando para la barra de progreso de la cinta de opciones.

*nAncho*<br/>
[en] Especifica el ancho, en píxeles, de la barra de progreso de la cinta de opciones.

*nAltura*<br/>
[en] Especifica la altura, en píxeles, de la barra de progreso de la cinta de opciones.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos

Devuelve la posición actual de la barra de progreso.

```
int GetPos () const;
```

### <a name="return-value"></a>Valor devuelto

Valor que representa la posición actual de la barra de progreso.

### <a name="remarks"></a>Observaciones

El intervalo que se establece debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax

Devuelve el valor máximo actual de la barra de progreso.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

El valor máximo del rango actual.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin

Devuelve el valor de intervalo mínimo actual de la barra de progreso.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

El valor mínimo del rango actual.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode

Especifica si la barra de progreso funciona en modo infinito.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la barra de progreso está en modo infinito; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

En el modo infinito, la barra de progreso se rellena repetidamente desde el valor mínimo hasta el valor máximo. Puede usar el modo infinito para indicar que una operación está en curso, pero que el tiempo de finalización es desconocido.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode

Establece la barra de progreso para que funcione en modo infinito.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bset*<br/>
[en] TRUE para especificar que la barra de progreso está en modo infinito; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Normalmente, si la barra de progreso está en modo infinito, indica al usuario que una operación está en curso, pero que se desconoce el tiempo de finalización. Por lo tanto, la barra de progreso se rellena repetidamente desde el valor mínimo hasta el valor máximo.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos

Establece la posición actual de la barra de progreso.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
[en] Especifica la posición en la que se establece la barra de progreso.

*bRedraw*<br/>
[en] Especifica si se debe volver a dibujar la barra de progreso.

### <a name="remarks"></a>Observaciones

El intervalo que se establece debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange

Establece los valores mínimo y máximo para la barra de progreso.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
[en] Especifica el valor mínimo del intervalo.

*nMax*<br/>
[en] Especifica el valor máximo del intervalo.

### <a name="remarks"></a>Observaciones

Utilice este método para definir el intervalo de la barra de progreso estableciendo valores mínimos y máximos.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement Clase](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
