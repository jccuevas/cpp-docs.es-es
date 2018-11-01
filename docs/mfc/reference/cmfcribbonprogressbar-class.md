---
title: CMFCRibbonProgressBar (clase)
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
ms.openlocfilehash: 13d73b09fc9fb88736242e7d0c04c33baa795914
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608604"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar (clase)

Implementa un control que indica visualmente el progreso de una operación larga.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Construye e inicializa un objeto `CMFCRibbonProgressBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Devuelve el progreso actual.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Devuelve el valor máximo del intervalo actual.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del intervalo actual.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Especifica si la barra de progreso está funcionando en modo de infinito.|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [cmfcribbonbaseelement:: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Establece la barra de progreso para trabajar en modo infinito.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Establece el progreso actual.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Establece los valores mínimos y máximo.|

## <a name="remarks"></a>Comentarios

Un `CMFCRibbonProgressBar` puede funcionar en dos modos: normal e infinito. En el modo normal, la barra de progreso se rellena de izquierda a derecha y se detiene cuando alcanza el valor máximo. En el modo infinito, la barra de progreso se rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonProgressBar` . El ejemplo muestra cómo establecer la barra de progreso para trabajar en modo infinito (donde el tiempo de finalización de una operación es desconocido), establezca los valores mínimos y máximo de la barra de progreso y establecer la posición actual de la barra de progreso. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonProgressBar.h

##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar

Crea e inicializa un [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objeto.

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[in] Especifica el identificador de comando de la barra de progreso de la cinta de opciones.

*nWidth*<br/>
[in] Especifica el ancho, en píxeles, de la barra de progreso de la cinta de opciones.

*nHeight*<br/>
[in] Especifica el alto, en píxeles, de la barra de progreso de la cinta de opciones.

##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos

Devuelve la posición actual de la barra de progreso.

```
int GetPos () const;
```

### <a name="return-value"></a>Valor devuelto

Un valor que representa la posición actual de la barra de progreso.

### <a name="remarks"></a>Comentarios

El intervalo que se va a establecer debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.

##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax

Devuelve el actual de la barra de progreso del valor máximo.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

El valor máximo del intervalo actual.

### <a name="remarks"></a>Comentarios

##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin

Devuelve el actual de la barra de progreso del valor mínimo del intervalo.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

El valor mínimo del intervalo actual.

##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[in] *pDC*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode

Especifica si la barra de progreso está funcionando en modo de infinito.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la barra de progreso está en modo de infinito; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En el modo infinito, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.

##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[in] *pDC*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode

Establece la barra de progreso para trabajar en modo infinito.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSet*<br/>
[in] TRUE para especificar que la barra de progreso está en modo de infinito; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Por lo general, si la barra de progreso está en modo infinito, se indica al usuario que está en curso una operación, pero que la hora de finalización es desconocida. Por lo tanto, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo.

##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos

Establece la posición actual de la barra de progreso.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
[in] Especifica la posición a la que se establece la barra de progreso.

*bRedraw*<br/>
[in] Especifica si debe volver a dibujar la barra de progreso.

### <a name="remarks"></a>Comentarios

El intervalo que se va a establecer debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.

##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange

Establece los valores mínimos y máximo de la barra de progreso.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nmín.*<br/>
[in] Especifica el valor mínimo del intervalo.

*Nmáx.*<br/>
[in] Especifica el valor máximo del intervalo.

### <a name="remarks"></a>Comentarios

Utilice este método para definir el intervalo de la barra de progreso estableciendo los valores mínimos y máximo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement (clase)](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
