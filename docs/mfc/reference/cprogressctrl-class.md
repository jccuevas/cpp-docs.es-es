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
ms.openlocfilehash: c9e94e334318b32efcf8c9de681a78349ab12151
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751124"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (clase)

Proporciona la funcionalidad del control de barra de progreso común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construye un objeto `CProgressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CProgressCtrl::Create](#create)|Crea un control de barra de `CProgressCtrl` progreso y lo asocia a un objeto.|
|[CProgressCtrl::CreateEx](#createex)|Crea un control de progreso con los estilos `CProgressCtrl` extendidos de Windows especificados y lo asocia a un objeto.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtiene el color de la barra del indicador de progreso para el control de barra de progreso actual.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtiene el color de fondo de la barra de progreso actual.|
|[CProgressCtrl::GetPos](#getpos)|Obtiene la posición actual de la barra de progreso.|
|[CProgressCtrl::GetRange](#getrange)|Obtiene los límites inferior y superior del intervalo del control de barra de progreso.|
|[CProgressCtrl::GetState](#getstate)|Obtiene el estado del control de barra de progreso actual.|
|[CProgressCtrl::GetStep](#getstep)|Recupera el incremento de paso para la barra de progreso del control de barra de progreso actual.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Avanza la posición actual de un control de barra de progreso en un incremento especificado y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Establece el color de la barra del indicador de progreso en el control de barra de progreso actual.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de la barra de progreso.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Activa o desactiva el modo de marquesina para el control de barra de progreso actual.|
|[CProgressCtrl::SetPos](#setpos)|Establece la posición actual de un control de barra de progreso y vuelve a dibujar la barra para reflejar la nueva posición.|
|[CProgressCtrl::SetRange](#setrange)|Establece los rangos mínimo y máximo para un control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos rangos.|
|[CProgressCtrl::SetState](#setstate)|Establece el estado del control de la barra de progreso actual.|
|[CProgressCtrl::SetStep](#setstep)|Especifica el incremento de paso para un control de barra de progreso.|
|[CProgressCtrl::StepIt](#stepit)|Avanza la posición actual de un control de barra de progreso por el incremento de paso (consulte [SetStep](#setstep)) y vuelve a dibujar la barra para reflejar la nueva posición.|

## <a name="remarks"></a>Observaciones

Un control de barra de progreso es una ventana que una aplicación puede usar para indicar el progreso de una operación larga. Consiste en un rectángulo que se rellena gradualmente, de izquierda a derecha, con el color de resaltado del sistema a medida que avanza una operación.

Un control de barra de progreso tiene un rango y una posición actual. El rango representa la duración total de la operación y la posición actual representa el progreso que la aplicación ha realizado para completar la operación. El procedimiento de ventana utiliza el rango y la posición actual para determinar el porcentaje de la barra de progreso que se va a rellenar con el color de resaltado. Dado que los valores de rango y posición actual se expresan como enteros con signo, el rango posible de valores de posición actuales es de -2,147,483,648 a 2,147,483,647 inclusive.

Para obtener más `CProgressCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

Construye un objeto `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Observaciones

Después de `CProgressCtrl` construir `CProgressCtrl::Create` el objeto, llame para crear el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::Create

Crea un control de barra de `CProgressCtrl` progreso y lo asocia a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplique cualquier combinación de estilos de ventana descritos en [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK, además de los siguientes estilos de control de barra de progreso, al control:

- PBS_VERTICAL Muestra la información de progreso verticalmente, de arriba a abajo. Sin esta marca, el control de la barra de progreso se muestra horizontalmente, de izquierda a derecha.

- PBS_SMOOTH Muestra un relleno gradual y suave en el control de la barra de progreso. Sin esta marca, el control se llenará con bloques.

*Rect*<br/>
Especifica el tamaño y la posición del control de barra de progreso. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura. Dado que el control debe ser una ventana secundaria, las coordenadas especificadas son relativas al área de cliente de *pParentWnd*.

*pParentWnd*<br/>
Especifica la ventana primaria del control de `CDialog`barra de progreso, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de barra de progreso.

### <a name="return-value"></a>Valor devuelto

TRUESi `CProgressCtrl` el objeto se crea correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Construir un `CProgressCtrl` objeto en dos pasos. En primer lugar, llame `CProgressCtrl` al constructor, `Create`que crea el objeto y, a continuación, llame a , que crea el control de barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::CreateEx

Crea un control (una ventana secundaria) `CProgressCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de barra de progreso. Aplique cualquier combinación de estilos de ventana descritos en [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*Rect*<br/>
Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::GetBarColor

Obtiene el color de la barra del indicador de progreso para el control de barra de progreso actual.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color de la barra de progreso actual, representado como un valor [COLORREF,](/windows/win32/gdi/colorref) o CLR_DEFAULT si el color de la barra del indicador de progreso es el color predeterminado.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje PBM_GETBARCOLOR,](/windows/win32/Controls/pbm-getbarcolor) que se describe en el Windows SDK.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

Obtiene el color de fondo de la barra de progreso actual.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color de fondo de la barra de progreso actual, representado como un valor [COLORREF.](/windows/win32/gdi/colorref)

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje PBM_GETBKCOLOR,](/windows/win32/Controls/pbm-getbkcolor) que se describe en el Windows SDK.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::GetPos

Recupera la posición actual de la barra de progreso.

```
int GetPos();
```

### <a name="return-value"></a>Valor devuelto

La posición del control de la barra de progreso.

### <a name="remarks"></a>Observaciones

La posición del control de la barra de progreso no es la ubicación física en la pantalla, sino que está entre el rango superior e inferior indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl::GetRange

Obtiene los límites inferior y superior actual, o rango, del control de barra de progreso.

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower*<br/>
Una referencia a un entero que recibe el límite inferior del control de barra de progreso.

*nUpper*<br/>
Una referencia a un entero que recibe el límite superior del control de barra de progreso.

### <a name="remarks"></a>Observaciones

Esta función copia los valores de los límites inferior y superior a los enteros a los que hace referencia *nLower* y *nUpper*, respectivamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::GetState

Obtiene el estado del control de barra de progreso actual.

```
int GetState() const;
```

### <a name="return-value"></a>Valor devuelto

El estado del control de barra de progreso actual, que es uno de los siguientes valores:

|Value|State|
|-----------|-----------|
|PBST_NORMAL|En curso|
|PBST_ERROR|Error|
|PBST_PAUSED|En pausa|

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje PBM_GETSTATE,](/windows/win32/Controls/pbm-getstate) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el estado del control de barra de progreso actual.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl::GetStep

Recupera el incremento de paso para la barra de progreso del control de barra de progreso actual.

```
int GetStep() const;
```

### <a name="return-value"></a>Valor devuelto

El incremento de paso de la barra de progreso.

### <a name="remarks"></a>Observaciones

El incremento de paso es la cantidad por la que una llamada a [CProgressCtrl::StepIt](#stepit) aumenta la posición actual de la barra de progreso.

Este método envía el [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) mensaje, que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el incremento de paso del control de barra de progreso actual.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::OffsetPos

Avanza la posición actual del control de barra de progreso por el incremento especificado por *nPos* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Cantidad para adelantar la posición.

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de la barra de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::SetBarColor

Establece el color de la barra del indicador de progreso en el control de barra de progreso actual.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*clrBar*|[en] Un valor [COLORREF](/windows/win32/gdi/colorref) que especifica el nuevo color de la barra del indicador de progreso. Especifique CLR_DEFAULT para que la barra de progreso utilice su color predeterminado.|

### <a name="return-value"></a>Valor devuelto

El color anterior de la barra del indicador de progreso, representado como un valor [COLORREF,](/windows/win32/gdi/colorref) o CLR_DEFAULT si el color de la barra del indicador de progreso es el color predeterminado.

### <a name="remarks"></a>Observaciones

El `SetBarColor` método establece el color de la barra de progreso solo si un [tema](/windows/win32/Controls/visual-styles-overview) de Windows Vista no está en vigor.

Este método envía el [mensaje PBM_SETBARCOLOR,](/windows/win32/Controls/pbm-setbarcolor) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cambia el color de la barra de progreso a rojo, verde, azul o el valor predeterminado.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

Establece el color de fondo de la barra de progreso.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parámetros

*clrNew*<br/>
Un valor COLORREF que especifica el nuevo color de fondo. Especifique el valor de CLR_DEFAULT para utilizar el color de fondo predeterminado para la barra de progreso.

### <a name="return-value"></a>Valor devuelto

El valor [COLORREF](/windows/win32/gdi/colorref) que indica el color de fondo anterior o CLR_DEFAULT si el color de fondo es el color predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

Activa o desactiva el modo de marquesina para el control de barra de progreso actual.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fMarqueeMode*|[en] TRUE para activar el modo de marquesina o FALSE para desactivar el modo de marquesina.|
|*nInterval*|[en] Tiempo en milisegundos entre las actualizaciones de la animación de marquesina.|

### <a name="return-value"></a>Valor devuelto

Este método siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Cuando el modo marco está activado, la barra de progreso se anima y se desplaza como un signo en una carpa de cine.

Este método envía el [mensaje PBM_SETMARQUEE,](/windows/win32/Controls/pbm-setmarquee) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se inicia y detiene la animación de desplazamiento de marco.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

Establece la posición actual del control de barra de progreso según lo especificado por *nPos* y vuelve a dibujar la barra para reflejar la nueva posición.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Nueva posición del control de la barra de progreso.

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de la barra de progreso.

### <a name="remarks"></a>Observaciones

La posición del control de la barra de progreso no es la ubicación física en la pantalla, sino que está entre el rango superior e inferior indicado en [SetRange](#setrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::SetRange

Establece los límites superior e inferior del rango del control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos rangos.

```cpp
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

### <a name="remarks"></a>Observaciones

La función `SetRange32` miembro establece el intervalo de 32 bits para el control de progreso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::SetState

Establece el estado del control de la barra de progreso actual.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iState*|[en] El estado para establecer la barra de progreso. Utilice uno de los valores siguientes:<br /><br /> - PBST_NORMAL - En curso<br />- PBST_ERROR - Error<br />- PBST_PAUSED - En pausa|

### <a name="return-value"></a>Valor devuelto

El estado anterior del control de la barra de progreso actual.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje PBM_SETSTATE,](/windows/win32/Controls/pbm-setstate) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Ejemplo

El siguiente ejemplo de código establece el estado del control de la de barra de progreso actual como En pausa o En curso.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::SetStep

Especifica el incremento de paso para un control de barra de progreso.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parámetros

*nStep*<br/>
Nuevo incremento de paso.

### <a name="return-value"></a>Valor devuelto

Incremento del paso anterior.

### <a name="remarks"></a>Observaciones

El incremento de paso es la `CProgressCtrl::StepIt` cantidad por la que una llamada para aumentar la posición actual de la barra de progreso.

El incremento de paso predeterminado es 10.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::StepIt

Avanza la posición actual de un control de barra de progreso por el incremento de paso y vuelve a dibujar la barra para reflejar la nueva posición.

```
int StepIt();
```

### <a name="return-value"></a>Valor devuelto

La posición anterior del control de la barra de progreso.

### <a name="remarks"></a>Observaciones

El incremento de paso `CProgressCtrl::SetStep` se establece mediante la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
