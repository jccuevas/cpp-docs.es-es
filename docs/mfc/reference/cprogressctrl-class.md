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
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502851"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (clase)

Proporciona la funcionalidad del control de barra de progreso común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construye un objeto `CProgressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CProgressCtrl::Create](#create)|Crea un control de barra de progreso y lo adjunta a `CProgressCtrl` un objeto.|
|[CProgressCtrl::CreateEx](#createex)|Crea un control de progreso con los estilos extendidos de Windows especificados y lo `CProgressCtrl` adjunta a un objeto.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtiene el color de la barra de indicador de progreso para el control de barra de progreso actual.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtiene el color de fondo de la barra de progreso actual.|
|[CProgressCtrl::GetPos](#getpos)|Obtiene la posición actual de la barra de progreso.|
|[CProgressCtrl::GetRange](#getrange)|Obtiene los límites inferior y superior del intervalo del control de barra de progreso.|
|[CProgressCtrl::GetState](#getstate)|Obtiene el estado del control de barra de progreso actual.|
|[CProgressCtrl::GetStep](#getstep)|Recupera el incremento de paso de la barra de progreso del control de barra de progreso actual.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Hace avanzar la posición actual de un control de barra de progreso en un incremento especificado y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Establece el color de la barra de indicador de progreso en el control de la barra de progreso actual.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de la barra de progreso.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Activa o desactiva el modo de Marquesina para el control de barra de progreso actual.|
|[CProgressCtrl::SetPos](#setpos)|Establece la posición actual de un control de barra de progreso y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetRange](#setrange)|Establece los intervalos mínimo y máximo de un control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.|
|[CProgressCtrl::SetState](#setstate)|Establece el estado del control de la barra de progreso actual.|
|[CProgressCtrl::SetStep](#setstep)|Especifica el incremento de paso de un control de barra de progreso.|
|[CProgressCtrl::StepIt](#stepit)|Avanza la posición actual de un control de barra de progreso en el incremento de paso (vea [SetStep](#setstep)) y vuelve a dibujar la barra para reflejar la nueva posición.|

## <a name="remarks"></a>Comentarios

Un control de barra de progreso es una ventana que una aplicación puede utilizar para indicar el progreso de una operación larga. Consta de un rectángulo que se rellena gradualmente, de izquierda a derecha, con el color de resaltado del sistema a medida que una operación progresa.

Un control de barra de progreso tiene un intervalo y una posición actual. El intervalo representa la duración total de la operación y la posición actual representa el progreso que ha realizado la aplicación para completar la operación. El procedimiento de ventana usa el rango y la posición actual para determinar el porcentaje de la barra de progreso que se va a rellenar con el color de resaltado. Dado que los valores de intervalo y posición actual se expresan como enteros con signo, el intervalo posible de valores de posición actual es de-2.147.483.648 a 2.147.483.647, ambos incluidos.

Para obtener más información sobre `CProgressCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CProgressCtrl](../../mfc/using-cprogressctrl.md).

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

Después de construir el `CProgressCtrl` objeto, llame `CProgressCtrl::Create` a para crear el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>  CProgressCtrl::Create

Crea un control de barra de progreso y lo adjunta a `CProgressCtrl` un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplique cualquier combinación de stylesdescribed de ventana en [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK, además de los siguientes estilos de control de barra de progreso, al control:

- PBS_VERTICAL muestra la información de progreso verticalmente, de arriba abajo. Sin esta marca, el control de barra de progreso se muestra horizontalmente de izquierda a derecha.

- PBS_SMOOTH muestra el rellenado gradual y suave en el control de barra de progreso. Sin esta marca, el control se rellenará con los bloques.

*rect*<br/>
Especifica el tamaño y la posición del control de barra de progreso. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) . Dado que el control debe ser una ventana secundaria, las coordenadas especificadas son relativas al área cliente del *pParentWnd*.

*pParentWnd*<br/>
Especifica la ventana primaria del control de barra de progreso, `CDialog`normalmente una. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de barra de progreso.

### <a name="return-value"></a>Valor devuelto

True si el `CProgressCtrl` objeto se ha creado correctamente; de lo contrario, false.

### <a name="remarks"></a>Comentarios

Un `CProgressCtrl` objeto se crea en dos pasos. En primer lugar, llame al constructor, que `CProgressCtrl` crea el objeto y, `Create`a continuación, llame a, que crea el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>  CProgressCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CProgressCtrl` objeto.

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
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplique cualquier combinación de estilos de ventana descrita en [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el **WS_EX_** de estilo extendido de Windows.

##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor

Obtiene el color de la barra de indicador de progreso para el control de barra de progreso actual.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valor devuelto

Color de la barra de progreso actual, representada como un valor de [COLORREF](/windows/win32/gdi/colorref) , o CLR_DEFAULT si el color de la barra del indicador de progreso es el color predeterminado.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) , que se describe en el Windows SDK.

##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor

Obtiene el color de fondo de la barra de progreso actual.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Color de fondo de la barra de progreso actual, representado como un valor de [COLORREF](/windows/win32/gdi/colorref) .

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) , que se describe en el Windows SDK.

##  <a name="getpos"></a>  CProgressCtrl::GetPos

Recupera la posición actual de la barra de progreso.

```
int GetPos();
```

### <a name="return-value"></a>Valor devuelto

Posición del control de barra de progreso.

### <a name="remarks"></a>Comentarios

La posición del control de barra de progreso no es la ubicación física en la pantalla, sino entre el intervalo superior e inferior indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>  CProgressCtrl::GetRange

Obtiene los límites inferior y superior actuales, o el intervalo, del control de barra de progreso.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower*<br/>
Referencia a un entero que recibe el límite inferior del control de barra de progreso.

*nUpper*<br/>
Referencia a un entero que recibe el límite superior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

Esta función copia los valores de los límites inferior y superior a los enteros a los que hace referencia *nLower* y *nUpper*, respectivamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>  CProgressCtrl::GetState

Obtiene el estado del control de barra de progreso actual.

```
int GetState() const;
```

### <a name="return-value"></a>Valor devuelto

El estado del control de barra de progreso actual, que es uno de los valores siguientes:

|Valor|Estado|
|-----------|-----------|
|PBST_NORMAL|En curso|
|PBST_ERROR|Error|
|PBST_PAUSED|En pausa|

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) , que se describe en el Windows SDK.

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

Incremento de paso de la barra de progreso.

### <a name="remarks"></a>Comentarios

El incremento de paso es la cantidad por la que una llamada a [CProgressCtrl:: StepIt](#stepit) aumenta la posición actual de la barra de progreso.

Este método envía el mensaje [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el incremento de paso del control de barra de progreso actual.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos

Hace avanzar la posición actual del control de barra de progreso por el incremento especificado por *NPOs* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Cantidad que se va a avanzar la posición.

### <a name="return-value"></a>Valor devuelto

Posición anterior del control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor

Establece el color de la barra de indicador de progreso en el control de la barra de progreso actual.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*clrBar*|de Valor de [COLORREF](/windows/win32/gdi/colorref) que especifica el nuevo color de la barra del indicador de progreso. Especifique CLR_DEFAULT para que la barra de progreso use su color predeterminado.|

### <a name="return-value"></a>Valor devuelto

El color anterior de la barra del indicador de progreso, representado como un valor [COLORREF](/windows/win32/gdi/colorref) , o CLR_DEFAULT si el color de la barra indicadora de progreso es el color predeterminado.

### <a name="remarks"></a>Comentarios

El `SetBarColor` método establece el color de la barra de progreso solo si no hay ningún [tema](/windows/win32/Controls/visual-styles-overview) de Windows Vista en vigor.

Este método envía el mensaje [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) , que se describe en el Windows SDK.

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
Valor COLORREF que especifica el nuevo color de fondo. Especifique el valor de CLR_DEFAULT para usar el color de fondo predeterminado de la barra de progreso.

### <a name="return-value"></a>Valor devuelto

El valor [COLORREF](/windows/win32/gdi/colorref) que indica el color de fondo anterior, o CLR_DEFAULT si el color de fondo es el color predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee

Activa o desactiva el modo de Marquesina para el control de barra de progreso actual.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*fMarqueeMode*|de TRUE para activar el modo de marquesina o FALSE para desactivar el modo de marquesina.|
|*nInterval*|de Tiempo en milisegundos entre las actualizaciones de la animación de marquesina.|

### <a name="return-value"></a>Valor devuelto

Este método siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Cuando se activa el modo de marquesina, la barra de progreso se anima y se desplaza como un signo en una marquesina de teatro.

Este método envía el mensaje [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se inicia y se detiene la animación de desplazamiento de marquesina.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>  CProgressCtrl::SetPos

Establece la posición actual del control de barra de progreso según lo especificado por *NPOs* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Nueva posición del control de barra de progreso.

### <a name="return-value"></a>Valor devuelto

Posición anterior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

La posición del control de barra de progreso no es la ubicación física en la pantalla, sino entre el intervalo superior e inferior indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>  CProgressCtrl::SetRange

Establece los límites superior e inferior del intervalo del control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.

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
Especifica el límite inferior del intervalo (el valor predeterminado es cero).

*nUpper*<br/>
Especifica el límite superior del intervalo (el valor predeterminado es 100).

### <a name="remarks"></a>Comentarios

La función `SetRange32` miembro establece el intervalo de 32 bits para el control de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>  CProgressCtrl::SetState

Establece el estado del control de la barra de progreso actual.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iState*|de Estado en el que se va a establecer la barra de progreso. Utilice uno de los siguientes valores:<br /><br /> -PBST_NORMAL: en curso<br />-PBST_ERROR: error<br />-PBST_PAUSED: en pausa|

### <a name="return-value"></a>Valor devuelto

El estado anterior del control de la barra de progreso actual.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) , que se describe en el Windows SDK.

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
Nuevo incremento de paso.

### <a name="return-value"></a>Valor devuelto

Incremento del paso anterior.

### <a name="remarks"></a>Comentarios

El incremento de paso es la cantidad por la que una `CProgressCtrl::StepIt` llamada a aumenta la posición actual de la barra de progreso.

El incremento de paso predeterminado es 10.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>  CProgressCtrl::StepIt

Avanza la posición actual de un control de barra de progreso en el incremento del paso y vuelve a dibujar la barra para reflejar la nueva posición.

```
int StepIt();
```

### <a name="return-value"></a>Valor devuelto

Posición anterior del control de barra de progreso.

### <a name="remarks"></a>Comentarios

La función `CProgressCtrl::SetStep` miembro establece el incremento de paso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
