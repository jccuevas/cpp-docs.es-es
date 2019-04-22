---
title: CProgressCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: 15241485278f09d16c86fc7274f2fc1d85a7a2f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778954"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (clase)

Proporciona la funcionalidad del control de barra de progreso común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construye un objeto `CProgressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CProgressCtrl::Create](#create)|Crea un control de barra de progreso y la conecta a un `CProgressCtrl` objeto.|
|[CProgressCtrl::CreateEx](#createex)|Crea un control de progreso con los estilos extendidos de Windows especificados y lo asocia a un `CProgressCtrl` objeto.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtiene el color de la barra indicadora de progreso para el control de barra de progreso actual.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtiene el color de fondo de la barra de progreso actual.|
|[CProgressCtrl::GetPos](#getpos)|Obtiene la posición actual de la barra de progreso.|
|[CProgressCtrl::GetRange](#getrange)|Obtiene los límites superiores e inferiores del intervalo de control de la barra de progreso.|
|[CProgressCtrl::GetState](#getstate)|Obtiene el estado del control de barra de progreso actual.|
|[CProgressCtrl::GetStep](#getstep)|Recupera el incremento de paso de la barra de progreso del control de barra de progreso actual.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Hace avanzar la posición actual de un control de barra de progreso en un incremento especificado y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Establece el color de la barra indicadora de progreso en el control de barra de progreso actual.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de la barra de progreso.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Desactiva el modo de marquesina activado o desactivado para el control de barra de progreso actual.|
|[CProgressCtrl::SetPos](#setpos)|Establece la posición actual para un control de barra de progreso y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetRange](#setrange)|Establece los intervalos mínimos y máximo para un control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.|
|[CProgressCtrl::SetState](#setstate)|Establece el estado del control de la barra de progreso actual.|
|[CProgressCtrl::SetStep](#setstep)|Especifica el incremento de paso de un control de barra de progreso.|
|[CProgressCtrl::StepIt](#stepit)|Hace avanzar la posición actual para un control de barra de progreso en el incremento del paso (vea [SetStep](#setstep)) y vuelve a dibujar la barra para reflejar la nueva posición.|

## <a name="remarks"></a>Comentarios

Un control de barra de progreso es una ventana que una aplicación puede utilizar para indicar el progreso de una operación larga. Consta de un rectángulo que se rellena gradualmente, de izquierda a derecha, con el sistema de color de resaltado como que una operación progresa.

Un control de barra de progreso tiene un intervalo y una posición actual. El intervalo representa la duración total de la operación y la posición actual representa el progreso de que la aplicación se ha realizado para completar la operación. El procedimiento de ventana usa el intervalo y la posición actual para determinar el porcentaje de la barra de progreso que se rellena con el color de resaltado. Porque el intervalo y los valores actuales de posición se expresan como enteros con signo, el intervalo posible de los valores de posición actual es de -2.147.483.648 a 2.147.483.647 inclusive.

Para obtener más información sobre el uso de `CProgressCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl

Construye un objeto `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Comentarios

Después de crear el `CProgressCtrl` de objeto, llame a `CProgressCtrl::Create` para crear el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>  CProgressCtrl::Create

Crea un control de barra de progreso y la conecta a un `CProgressCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplicar cualquier combinación de ventana stylesdescribed en [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) en el SDK de Windows, además de la barra de estilos de control, para el control de progreso siguiente:

- PBS_VERTICAL muestra información de progreso vertical, de arriba a abajo. Sin esta marca, el control de barra de progreso muestra horizontalmente, de izquierda a derecha.

- PBS_SMOOTH muestra gradual smooth rellenando el control de barra de progreso. Sin esta marca, el control se llenará de bloques.

*rect*<br/>
Especifica el tamaño y la posición del control de barra de progreso. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura. Dado que el control debe ser una ventana secundaria, las coordenadas especificadas están en relación con el área cliente de la *pParentWnd*.

*pParentWnd*<br/>
Especifica el progreso de la barra de la ventana primaria de control, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de barra de progreso

### <a name="return-value"></a>Valor devuelto

TRUE si el `CProgressCtrl` objeto se creó correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Construir un `CProgressCtrl` objeto en dos pasos. En primer lugar, llame al constructor, que crea el `CProgressCtrl` objeto y, a continuación, llame a `Create`, que crea el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>  CProgressCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia a la `CProgressCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplicar cualquier combinación de estilos de ventana se describe en [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) en el SDK de Windows.

*rect*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor

Obtiene el color de la barra indicadora de progreso para el control de barra de progreso actual.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color de la barra de progreso actual, representado como un [COLORREF](/windows/desktop/gdi/colorref) valor o CLR_DEFAULT si el color de la barra del indicador de progreso es el color predeterminado.

### <a name="remarks"></a>Comentarios

Este método envía el [PBM_GETBARCOLOR](/windows/desktop/Controls/pbm-getbarcolor) mensaje, que se describe en el SDK de Windows.

##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor

Obtiene el color de fondo de la barra de progreso actual.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Representa el color de fondo de la barra de progreso actual, como un [COLORREF](/windows/desktop/gdi/colorref) valor.

### <a name="remarks"></a>Comentarios

Este método envía el [PBM_GETBKCOLOR](/windows/desktop/Controls/pbm-getbkcolor) mensaje, que se describe en el SDK de Windows.

##  <a name="getpos"></a>  CProgressCtrl::GetPos

Recupera la posición actual de la barra de progreso.

```
int GetPos();
```

### <a name="return-value"></a>Valor devuelto

La posición del control de barra de progreso.

### <a name="remarks"></a>Comentarios

La posición del control de barra de progreso no es la ubicación física en la pantalla, pero en su lugar entre la parte superior e inferior intervalo indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>  CProgressCtrl::GetRange

Obtiene los límites inferior y superior actuales, o intervalo, del control de barra de progreso.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower*<br/>
Una referencia a un entero que recibe el límite inferior del control de barra de progreso.

*nUpper*<br/>
Una referencia a un entero que recibe el límite superior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

Esta función copia los valores de los límites superiores e inferiores para los enteros que se hace referencia a *nLower* y *nUpper*, respectivamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>  CProgressCtrl::GetState

Obtiene el estado del control de barra de progreso actual.

```
int GetState() const;
```

### <a name="return-value"></a>Valor devuelto

El estado del control de barra de progreso actual, que es uno de los siguientes valores:

|Valor|Estado|
|-----------|-----------|
|PBST_NORMAL|En curso|
|PBST_ERROR|Error|
|PBST_PAUSED|En pausa|

### <a name="remarks"></a>Comentarios

Este método envía el [PBM_GETSTATE](/windows/desktop/Controls/pbm-getstate) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el estado del control de barra de progreso actual.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>  CProgressCtrl::GetStep

Recupera el incremento de paso de la barra de progreso del control de barra de progreso actual.

```
int GetStep() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento del paso de la barra de progreso.

### <a name="remarks"></a>Comentarios

El incremento de paso es la cantidad por la que una llamada a [CProgressCtrl::StepIt](#stepit) incrementa la posición actual de la barra de progreso.

Este método envía el [PBM_GETSTEP](/windows/desktop/Controls/pbm-getstep) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente recupera el incremento del paso del control de barra de progreso actual.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos

Hace avanzar la posición actual del control de barra de progreso en el incremento especificado por *nPos* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Cantidad de avanzar la posición.

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor

Establece el color de la barra indicadora de progreso en el control de barra de progreso actual.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*clrBar*|[in] Un [COLORREF](/windows/desktop/gdi/colorref) valor que especifica el nuevo color de la barra indicadora de progreso. Especifique CLR_DEFAULT para hacer que la barra de progreso usar su color predeterminado.|

### <a name="return-value"></a>Valor devuelto

Representa el color anterior de la barra del indicador de progreso, como un [COLORREF](/windows/desktop/gdi/colorref) valor o CLR_DEFAULT si el color de la barra indicadora de progreso es el color predeterminado.

### <a name="remarks"></a>Comentarios

El `SetBarColor` método establece el progreso de la barra solo si de color una Vista de Windows [tema](/windows/desktop/Controls/visual-styles-overview) no está en vigor.

Este método envía el [PBM_SETBARCOLOR](/windows/desktop/Controls/pbm-setbarcolor) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cambia el color de la barra de progreso a rojo, verde, azul o el valor predeterminado.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor

Establece el color de fondo de la barra de progreso.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parámetros

*clrNew*<br/>
Un valor COLORREF que especifica el nuevo color de fondo. Especifique el valor CLR_DEFAULT para usar el color de fondo predeterminado para la barra de progreso.

### <a name="return-value"></a>Valor devuelto

El [COLORREF](/windows/desktop/gdi/colorref) valor que indica el color de fondo anterior o CLR_DEFAULT si el color de fondo es el color predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee

Desactiva el modo de marquesina activado o desactivado para el control de barra de progreso actual.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fMarqueeMode*|[in] True para activar el modo de marquesina en, o FALSE para desactivar el modo de marquesina.|
|*nInterval*|[in] Tiempo en milisegundos entre las actualizaciones de la animación de marquesina.|

### <a name="return-value"></a>Valor devuelto

Este método siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Cuando está activado el modo de marquesina, se anima la barra de progreso y se desplaza al igual que un inicio de sesión en un recuadro de pantalla completa.

Este método envía el [PBM_SETMARQUEE](/windows/desktop/Controls/pbm-setmarquee) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente se inicia y detiene la animación de desplazamiento de marquesina.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>  CProgressCtrl::SetPos

Establece el progreso de la posición actual del control especificado por la barra *nPos* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Nueva posición del control de barra de progreso.

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

La posición del control de barra de progreso no es la ubicación física en la pantalla, pero en su lugar entre la parte superior e inferior intervalo indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>  CProgressCtrl::SetRange

Establece los límites superiores e inferiores de la barra de intervalo del control de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower*<br/>
Especifica el límite inferior del intervalo (valor predeterminado es cero).

*nUpper*<br/>
Especifica el límite superior del intervalo (valor predeterminado es 100).

### <a name="remarks"></a>Comentarios

La función miembro `SetRange32` establece el rango de 32 bits para el control de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>  CProgressCtrl::SetState

Establece el estado del control de la barra de progreso actual.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iState*|[in] El estado para establecer la barra de progreso. Utilice uno de los siguientes valores:<br /><br /> -PBST_NORMAL - en curso<br />-PBST_ERROR - Error<br />-PBST_PAUSED - en pausa|

### <a name="return-value"></a>Valor devuelto

El estado anterior del control de la barra de progreso actual.

### <a name="remarks"></a>Comentarios

Este método envía el [PBM_SETSTATE](/windows/desktop/Controls/pbm-setstate) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código establece el estado del control de la de barra de progreso actual como En pausa o En curso.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>  CProgressCtrl::SetStep

Especifica el incremento de paso de un control de barra de progreso.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parámetros

*nStep*<br/>
Nuevo incremento del paso.

### <a name="return-value"></a>Valor devuelto

El incremento del paso anterior.

### <a name="remarks"></a>Comentarios

El incremento de paso es la cantidad por la que una llamada a `CProgressCtrl::StepIt` aumenta el progreso de la barra de la posición actual.

El incremento del paso predeterminado es 10.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>  CProgressCtrl::StepIt

Hace avanzar la posición actual para un control de barra de progreso en el incremento de paso y vuelve a dibujar la barra para reflejar la nueva posición.

```
int StepIt();
```

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

Establece el incremento del paso la `CProgressCtrl::SetStep` función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Vea también

[MFC Sample CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
