---
title: CMonthCalCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: da9d588811361d3dfd72d44d5b9ced8460d23936
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319752"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (clase)

Encapsula la funcionalidad de un control de calendario mensual.

## <a name="syntax"></a>Sintaxis

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Construye un objeto `CMonthCalCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMonthCalCtrl::Crear](#create)|Crea un control de calendario de `CMonthCalCtrl` mes y lo adjunta al objeto.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Recupera el ancho del borde del control de calendario del mes actual.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Recupera el número de calendarios que se muestran en el control de calendario del mes actual.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Recupera información sobre el control de calendario del mes actual.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Recupera el identificador de calendario para el control de calendario del mes actual.|
|[CMonthCalCtrl::GetColor](#getcolor)|Obtiene el color de un área especificada de un control de calendario de mes.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Recupera la vista que muestra actualmente el control de calendario del mes actual.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Recupera la hora del sistema como se indica en la fecha seleccionada actualmente.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario de mes.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Recupera el ancho máximo de la cadena "Hoy" para el control de calendario del mes actual.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario de mes.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Recupera la velocidad de desplazamiento de un control de calendario de mes.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Recupera información de fecha que representa los límites altos y bajos de la visualización de un control de calendario de mes.|
|[CMonthCalCtrl::GetRange](#getrange)|Recupera las fechas mínimas y máximas actuales establecidas en un control de calendario de mes.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Recupera información de fecha que representa los límites superior e inferior del intervalo de fechas seleccionado actualmente por el usuario.|
|[CMonthCalCtrl::GetToday](#gettoday)|Recupera la información de fecha para la fecha especificada como "hoy" para un control de calendario de mes.|
|[CMonthCalCtrl::HitTest](#hittest)|Determina qué sección de un control de calendario de mes se encuentra en un punto determinado de la pantalla.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indica si la vista actual del control de calendario del mes actual es la vista de siglo.|
|[CMonthCalCtrl::IsdecadeView](#isdecadeview)|Indica si la vista actual del control de calendario del mes actual es la vista de década.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indica si la vista actual del control de calendario del mes actual es la vista de mes.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Indica si la vista actual del control de calendario del mes actual es la vista de año.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Establece el ancho del borde del control de calendario del mes actual.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Establece el ancho predeterminado del borde del control de calendario del mes actual.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Establece el identificador de calendario para el control de calendario del mes actual.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Establece el control de calendario del mes actual para mostrar la vista de siglo.|
|[CMonthCalCtrl::SetColor](#setcolor)|Establece el color de un área especificada de un control de calendario de mes.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Establece el control de calendario del mes actual para mostrar la vista especificada.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Establece la fecha seleccionada actualmente para un control de calendario de mes.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Establece la visualización de los días de un control de calendario de mes.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Establece el control de calendario del mes actual en la vista de década.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Establece el día de la semana que se mostrará en la columna situada más a la izquierda del calendario.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Establece el número máximo de días que se pueden seleccionar en un control de calendario de mes.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Establece la velocidad de desplazamiento para un control de calendario de mes.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Establece el control de calendario del mes actual para mostrar la vista de mes.|
|[CMonthCalCtrl::SetRange](#setrange)|Establece las fechas mínimas y máximas permitidas para un control de calendario de mes.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Establece la selección de un control de calendario de mes en un intervalo de fechas determinado.|
|[CMonthCalCtrl::SetToday](#settoday)|Establece el control de calendario para el día actual.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Establece el control de calendario del mes actual en la vista de año.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Repinta el control de calendario de mes a su tamaño mínimo de un mes.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.|

## <a name="remarks"></a>Observaciones

El control de calendario de mes proporciona al usuario una interfaz de calendario simple, desde la que el usuario puede seleccionar una fecha. El usuario puede cambiar la pantalla por:

- Desplazamiento hacia atrás y hacia adelante, de mes a mes.

- Haga clic en el texto Hoy para mostrar el día actual (si no se utiliza el estilo de MCS_NOTODAY).

- Elegir un mes o un año en un menú emergente.

Puede personalizar el control de calendario de mes aplicando una variedad de estilos al objeto al crearlo. Estos estilos se describen en Estilos de control de calendario de [mes](/windows/win32/Controls/month-calendar-control-styles) en el Windows SDK.

El control de calendario de mes puede mostrar más de un mes y puede indicar días especiales (como días festivos) poniendo en negrita la fecha.

Para obtener más información sobre el uso del control de calendario de mes, vea Uso de [CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl

Construye un objeto `CMonthCalCtrl`.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Observaciones

Debe llamar `Create` después de construir el objeto.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Crear

Crea un control de calendario de `CMonthCalCtrl` mes y lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de Windows aplicados al control de calendario de mes. Consulte Estilos de control de calendario de [mes](/windows/win32/Controls/month-calendar-control-styles) en el Windows SDK para obtener más información acerca de los estilos.

*Rect*<br/>
Una referencia a una estructura [RECT.](/previous-versions/dd162897\(v=vs.85\)) Contiene la posición y el tamaño del control de calendario de mes.

*Pt*<br/>
Una referencia a una estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que identifica la ubicación del control de calendario de mes.

*pParentWnd*<br/>
Puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control de calendario de mes. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control de calendario de mes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cree un control de calendario de mes en dos pasos:

1. Llame a [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) para construir un `CMonthCalCtrl` objeto.

1. Llame a esta función miembro, que crea un `CMonthCalCtrl` control de calendario de mes y lo adjunta al objeto.

Cuando se `Create`llama a , se inicializan los controles comunes. La versión de `Create` la llamada determina cómo se dimensiona:

- Para que MFC ajuste automáticamente el tamaño del control a un mes, llame a la invalidación que usa *el* pt parámetro.

- Para dimensionar el control usted mismo, llame a la invalidación de esta función que utiliza el *rect* parámetro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder

Recupera el ancho del borde del control de calendario del mes actual.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho del borde del control, en píxeles.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje MCM_GETCALENDARBORDER,](/windows/win32/Controls/mcm-getcalendarborder) que se describe en el Windows SDK.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount

Recupera el número de calendarios que se muestran en el control de calendario del mes actual.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de calendarios que se muestran actualmente en el control de calendario de mes. El número máximo permitido de calendarios es 12.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje MCM_GETCALENDARCOUNT,](/windows/win32/Controls/mcm-getcalendarcount) que se describe en el Windows SDK.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo

Recupera información sobre el control de calendario del mes actual.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pmcGridInfo*|[fuera] Puntero a una estructura [MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) que recibe información sobre el control de calendario del mes actual. El autor de la llamada es responsable de asignar e inicializar esta estructura.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje MCM_GETCALENDARGRIDINFO,](/windows/win32/Controls/mcm-getcalendargridinfo) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo `GetCalendarGridInfo` de código siguiente se usa el método para recuperar la fecha de calendario que muestra el control de calendario de mes actual.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID

Recupera el identificador de calendario para el control de calendario del mes actual.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Valor devuelto

Una de las constantes de identificador de [calendario.](/windows/win32/Intl/calendar-identifiers)

### <a name="remarks"></a>Observaciones

Un identificador de calendario denota un calendario específico de la región, como los calendarios gregoriano (localizado), japonés o Hijri. La aplicación puede usar un identificador de calendario que tiene varias funciones de compatibilidad con el lenguaje.

Este método envía el [mensaje MCM_GETCALID,](/windows/win32/Controls/mcm-getcalid) que se describe en el Windows SDK.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor

Recupera el color de un área del control de calendario de mes especificado por *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parámetros

*nRegión*<br/>
La región del control de calendario del mes desde el que se recupera el color. Para obtener una lista de valores, vea el *nRegion* parámetro de [SetColor](#setcolor).

### <a name="return-value"></a>Valor devuelto

Un [colorREF](/windows/win32/gdi/colorref) valor que especifica el color asociado con la parte del control de calendario de mes, si se realiza correctamente. De lo contrario, esta función miembro devuelve -1.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView

Recupera la vista que muestra actualmente el control de calendario del mes actual.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Valor devuelto

La vista actual, que se indica mediante uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|MCMV_MONTH|Vista mensual|
|MCMV_YEAR|Vista anual|
|MCMV_DECADE|Vista de la década|
|MCMV_CENTURY|Vista del siglo|

### <a name="remarks"></a>Observaciones

Este método envía el [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) mensaje, que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se notifica qué ver el control de calendario de mes que se muestra actualmente.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel

Recupera la hora del sistema como se indica en la fecha seleccionada actualmente.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto. Recibe la hora actual.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que recibirá la información de fecha seleccionada actualmente. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; otherwize 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel), como se describe en el Windows SDK.

> [!NOTE]
> Esta función miembro produce un error si se establece el estilo MCS_MULTISELECT.

En la implementación `GetCurSel`de MFC `COleDateTime` de , `CTime` puede especificar `SYSTEMTIME` un uso, un uso o un uso de estructura.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek

Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parámetros

*pbLocal*<br/>
Un puntero a un valor BOOL. Si el valor es distinto de cero, la configuración del control no coincide con la configuración del panel de control.

### <a name="return-value"></a>Valor devuelto

Valor entero que representa el primer día de la semana. Consulte **Comentarios** para obtener más información sobre lo que representan estos enteros.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-getfirstdayofweek)Win32 MCM_GETFIRSTDAYOFWEEK , como se describe en el Windows SDK. Los días de la semana se representan como enteros, como se indica a continuación.

|Value|Día de la semana|
|-----------|---------------------|
|0|Lunes|
|1|Martes|
|2|Miércoles|
|3|Jueves|
|4|Viernes|
|5|Sábado|
|6|Domingo|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount

Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario de mes.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que representa el número total de días que se pueden seleccionar para el control.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount), como se describe en el Windows SDK. Utilice esta función miembro para los controles con el conjunto de estilos MCS_MULTISELECT.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth

Recupera el ancho máximo de la cadena "Hoy" para el control de calendario del mes actual.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho de la cadena "Hoy", en píxeles.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `GetMaxTodayWidth` código siguiente se muestra el método.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Observaciones

El usuario puede volver a la fecha actual haciendo clic en la cadena "Hoy", que se muestra en la parte inferior del control de calendario del mes. La cadena "Hoy" incluye texto de etiqueta y texto de fecha.

Este método envía el [mensaje MCM_GETMAXTODAYWIDTH,](/windows/win32/Controls/mcm-getmaxtodaywidth) que se describe en el Windows SDK.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect

Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario de mes.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parámetros

*pRect*<br/>
Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que recibirá información de rectángulo delimitador. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, esta `lpRect` función miembro devuelve distinto de cero y recibe la información de límite aplicable. Si no se realiza correctamente, la función miembro devuelve 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-getminreqrect)Win32 MCM_GETMINREQRECT , como se describe en el Windows SDK.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta

Recupera la velocidad de desplazamiento de un control de calendario de mes.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Valor devuelto

La velocidad de desplazamiento para el control de calendario de mes. La velocidad de desplazamiento es el número de meses que el control mueve su visualización cuando el usuario hace clic en un botón de desplazamiento una vez.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta), como se describe en el Windows SDK.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange

Recupera información de fecha que representa los límites altos y bajos de la visualización de un control de calendario de mes.

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>Parámetros

*refMinRange*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.

*refMaxRange*<br/>
Una referencia `COleDateTime` a `CTime` un objeto u objeto que contiene la fecha máxima permitida.

*pMinRange*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más bajo del intervalo.

*pMaxRange*<br/>
Puntero a `SYSTEMTIME` una estructura que contiene la fecha en el extremo más alto del intervalo.

*dwFlags*<br/>
Valor que especifica el ámbito de los límites de intervalo que se van a recuperar. Este valor debe ser uno de los siguientes.

|Value|Significado|
|-----------|-------------|
|GMR_DAYSTATE|Incluya los meses anteriores y finales del rango visible que solo se muestran parcialmente.|
|GMR_VISIBLE|Incluya solo los meses que se muestran por completo.|

### <a name="return-value"></a>Valor devuelto

Entero que representa el intervalo, en meses, abarcado por los dos límites indicados por *refMinRange* y *refMaxRange* en la primera y segunda versiones, o *pMinRange* y *pMaxRange* en la tercera versión.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-getmonthrange)Win32 MCM_GETMONTHRANGE , como se describe en el Windows SDK. En la implementación `GetMonthRange`de MFC `COleDateTime` de `CTime` , puede `SYSTEMTIME` especificar el uso, un uso o un uso de estructura.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl::SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange

Recupera las fechas mínimas y máximas actuales establecidas en un control de calendario de mes.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parámetros

*pMinRange*<br/>
Puntero a `COleDateTime` un objeto, un `CTime` objeto o estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más bajo del intervalo.

*pMaxRange*<br/>
Puntero a `COleDateTime` un objeto, un `CTime` objeto o estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más alto del intervalo.

### <a name="return-value"></a>Valor devuelto

Un DWORD que puede ser cero (no se establecen límites) o una combinación de los siguientes valores que especifican información de límite.

|Value|Significado|
|-----------|-------------|
|GDTR_MAX|Se establece un límite máximo para el control; *pMaxRange* es válido y contiene la información de fecha aplicable.|
|GDTR_MIN|Se establece un límite mínimo para el control; *pMinRange* es válido y contiene la información de fecha aplicable.|

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange), como se describe en el Windows SDK. En la implementación `GetRange`de MFC `COleDateTime` de , `CTime` puede especificar `SYSTEMTIME` un uso, un uso o un uso de estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange

Recupera información de fecha que representa los límites superior e inferior del intervalo de fechas seleccionado actualmente por el usuario.

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parámetros

*refMinRange*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.

*refMaxRange*<br/>
Una referencia `COleDateTime` a `CTime` un objeto u objeto que contiene la fecha máxima permitida.

*pMinRange*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más bajo del intervalo.

*pMaxRange*<br/>
Puntero a `SYSTEMTIME` una estructura que contiene la fecha en el extremo más alto del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange), como se describe en el Windows SDK. `GetSelRange`se producirá un error si se aplica a un control de calendario de mes que no usa el estilo MCS_MULTISELECT.

En la implementación `GetSelRange`de MFC `COleDateTime` de `CTime` , puede `SYSTEMTIME` especificar el uso, un uso o un uso de estructura.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday

Recupera la información de fecha para la fecha especificada como "hoy" para un control de calendario de mes.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el día actual.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que recibirá la información de fecha. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday), como se describe en el Windows SDK. En la implementación `GetToday`de MFC `COleDateTime` de , `CTime` puede especificar `SYSTEMTIME` un uso, un uso o un uso de estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest

Determina qué control de calendario de mes, si existe, se encuentra en una posición especificada.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parámetros

*pMCHitTest*<br/>
Puntero a una estructura [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) que contiene puntos de prueba de posicionamiento para el control de calendario de mes.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD. Igual que el miembro `MCHITTESTINFO` **uHit** de la estructura.

### <a name="remarks"></a>Observaciones

`HitTest`utiliza `MCHITTESTINFO` la estructura, que contiene información sobre la prueba de posicionamiento.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView

Indica si la vista actual del control de calendario del mes actual es la vista de siglo.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la vista actual es la vista de siglo; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) mensaje, que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_CENTURY, este método devuelve TRUE.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsdecadeView

Indica si la vista actual del control de calendario del mes actual es la vista de década.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la vista actual es la vista de la década; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) mensaje, que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_DECADE, este método devuelve TRUE.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView

Indica si la vista actual del control de calendario del mes actual es la vista de mes.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la vista actual es la vista de mes; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) mensaje, que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_MONTH, este método devuelve TRUE.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView

Indica si la vista actual del control de calendario del mes actual es la vista de año.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la vista actual es la vista de año; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) mensaje, que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_YEAR, este método devuelve TRUE.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder

Establece el ancho del borde del control de calendario del mes actual.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*cxyBorder*|[en] El ancho del borde, en píxeles.|

### <a name="remarks"></a>Observaciones

Si este método se realiza correctamente, el ancho del borde se establece en el *cxyBorder* parámetro. De lo contrario, el ancho del borde se restablece al valor predeterminado especificado por el [tema](/windows/win32/Controls/visual-styles-overview)actual, o cero si no se utilizan temas.

Este método envía el [mensaje MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el ancho del borde del control de calendario de mes en ocho píxeles. Utilice el [método CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) para determinar si este método se realizó correctamente.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault

Establece el ancho predeterminado del borde del control de calendario del mes actual.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Observaciones

El ancho del borde se establece en el valor predeterminado especificado por el [tema](/windows/win32/Controls/visual-styles-overview)actual, o cero si no se utilizan temas.

Este método envía el [mensaje MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) que se describe en el Windows SDK.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID

Establece el identificador de calendario para el control de calendario del mes actual.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*calid*|[en] Una de las constantes de identificador de [calendario.](/windows/win32/Intl/calendar-identifiers)|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Un identificador de calendario especifica un calendario específico de la región, como los calendarios gregoriano (localizado), japonés o Hijri. Utilice `SetCalID` el método para mostrar un calendario especificado por el parámetro *calid* si la configuración regional que contiene el calendario está instalado en el equipo.

Este método envía el [mensaje MCM_SETCALID,](/windows/win32/Controls/mcm-setcalid) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control de calendario de mes para mostrar el calendario de la Era del Emperador Japonés. El `SetCalID` método solo se realiza correctamente si ese calendario está instalado en el equipo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView

Establece el control de calendario del mes actual para mostrar la vista de siglo.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método utiliza el [método CMonthCalCtrl::SetCurrentView](#setcurrentview) para establecer la vista `MCMV_CENTURY`en , que representa la vista de siglo.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor

Establece el color de un área especificada de un control de calendario de mes.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*nRegión*<br/>
Valor entero que especifica el color del calendario del mes que se va a establecer. Este valor puede ser uno de los siguientes.

|Value|Significado|
|-----------|-------------|
|MCSC_BACKGROUND|El color de fondo que se muestra entre meses.|
|MCSC_MONTHBK|El color de fondo que se muestra dentro del mes.|
|MCSC_TEXT|El color utilizado para mostrar texto en el plazo de un mes.|
|MCSC_TITLEBK|El color de fondo que se muestra en el título del calendario.|
|MCSC_TITLETEXT|El color utilizado para mostrar texto dentro del título del calendario.|
|MCSC_TRAILINGTEXT|El color utilizado para mostrar el encabezado y el texto del día final. Los días de cabecera y de trailing son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|

*ref*<br/>
Un valor COLORREF para la nueva configuración de color para la parte especificada del control de calendario de mes.

### <a name="return-value"></a>Valor devuelto

Un colorREF valor que representa la configuración de color anterior para la parte especificada del control de calendario de mes, si se realiza correctamente. De lo contrario, este mensaje devuelve -1.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-setcolor)Win32 MCM_SETCOLOR , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView

Establece el control de calendario del mes actual para mostrar la vista especificada.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwNewView*|[en] Uno de los siguientes valores que especifica una vista mensual, anual, de década o de siglo.<br /><br /> MCMV_MONTH: Vista mensual<br /><br /> MCMV_YEAR: Vista anual<br /><br /> MCMV_DECADE: Vista de la década<br /><br /> MCMV_CENTURY: Vista del siglo|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje MCM_SETCURRENTVIEW,](/windows/win32/Controls/mcm-setcurrentview) que se describe en el Windows SDK.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel

Establece la fecha seleccionada actualmente para un control de calendario de mes.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el control de calendario de mes seleccionado actualmente.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha que se establecerá como la selección actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-setcursel)Win32 MCM_SETCURSEL , como se describe en el Windows SDK. En la implementación `SetCurSel`de MFC `COleDateTime` de , `CTime` puede especificar `SYSTEMTIME` un uso, un uso o un uso de estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl::SetDayState

Establece la visualización de los días de un control de calendario de mes.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parámetros

*nMeses*<br/>
Valor que indica cuántos elementos hay en la matriz a la que *apunta pStates.*

*pStates*<br/>
Puntero a una matriz [MONTHDAYSTATE](/windows/win32/Controls/monthdaystate) de valores que definen cómo se dibujará el control de calendario de mes cada día en su visualización. El tipo de datos MONTHDAYSTATE es un campo de bits, donde cada bit (1 a 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente se mostrará en negrita; de lo contrario se mostrará sin énfasis.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView

Establece el control de calendario del mes actual en la vista de década.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método utiliza el [Método CMonthCalCtrl::SetCurrentView](#setcurrentview) para establecer la vista en `MCMV_DECADE`, que representa la vista de década.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek

Establece el día de la semana que se mostrará en la columna situada más a la izquierda del calendario.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parámetros

*iDay*<br/>
Un valor entero que representa qué día se debe establecer como el primer día de la semana. Este valor debe ser uno de los números de día. Consulte [GetFirstDayOfWeek](#getfirstdayofweek) para obtener una descripción de los números de día.

*lpnOld*<br/>
Puntero a un entero que indica el primer día de la semana establecida anteriormente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el primer día anterior de la semana se establece en un valor distinto del de LOCALE_IFIRSTDAYOFWEEK, que es el día indicado en la configuración del panel de control. De lo contrario, esta función devuelve 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount

Establece el número máximo de días que se pueden seleccionar en un control de calendario de mes.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parámetros

*nMax*<br/>
El valor que se establecerá para representar el número máximo de días seleccionables.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-setmaxselcount)Win32 MCM_SETMAXSELCOUNT , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta

Establece la velocidad de desplazamiento para un control de calendario de mes.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parámetros

*iDelta*<br/>
El número de meses que se establecerá como la velocidad de desplazamiento del control. Si este valor es cero, el delta del mes se restablece al valor predeterminado, que es el número de meses que se muestra nalque en el control.

### <a name="return-value"></a>Valor devuelto

La velocidad de desplazamiento anterior. Si la velocidad de desplazamiento no se ha establecido previamente, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/mcm-setmonthdelta)Win32 MCM_SETMONTHDELTA , como se describe en el Windows SDK.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView

Establece el control de calendario del mes actual para mostrar la vista de mes.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método utiliza el [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista en MCMV_MONTH, que representa la vista de mes.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_monthCalCtrl`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de calendario de mes. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control de calendario de mes para mostrar las vistas de mes, año, década y siglo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange

Establece las fechas mínimas y máximas permitidas para un control de calendario de mes.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parámetros

*pMinRange*<br/>
Puntero a `COleDateTime` un objeto, un `CTime` objeto o estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más bajo del intervalo.

*pMaxRange*<br/>
Puntero a `COleDateTime` un objeto, `CTime` un `SYSTEMTIME` objeto o estructura que contiene la fecha en el extremo más alto del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange), como se describe en el Windows SDK. En la implementación `SetRange`de MFC `COleDateTime` de `CTime` , puede `SYSTEMTIME` especificar el uso, un uso o un uso de estructura.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl::GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange

Establece la selección de un control de calendario de mes en un intervalo de fechas determinado.

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parámetros

*pMinRange*<br/>
Puntero a `COleDateTime` un objeto, un `CTime` objeto o estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo más bajo del intervalo.

*pMaxRange*<br/>
Puntero a `COleDateTime` un objeto, `CTime` un `SYSTEMTIME` objeto o estructura que contiene la fecha en el extremo más alto del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange), como se describe en el Windows SDK. En la implementación `SetSelRange`de MFC `COleDateTime` de `CTime` , puede `SYSTEMTIME` especificar el uso, un uso o un uso de estructura.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday

Establece el control de calendario para el día actual.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha actual.

*pDateTime*<br/>
En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la información de fecha actual. En la tercera versión, un puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la información de fecha actual.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 MCM_SETTODAY](/windows/win32/Controls/mcm-settoday), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl::GetToday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView

Establece el control de calendario del mes actual en la vista de año.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método utiliza el [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista en MCMV_YEAR, que representa la vista anual.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq

Muestra el control de calendario de mes al tamaño mínimo que muestra un mes.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parámetros

*bRepaint*<br/>
Especifica si se va a volver a pintar el control. De forma predeterminada, TRUE. Si FALSE, no se produce ningún repintado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control de calendario de mes tiene el tamaño mínimo; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Al `SizeMinReq` llamar correctamente se muestra el control de calendario de todo el mes para el calendario de un mes.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin

Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpRect*|[en] Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que define un rectángulo que contiene el número deseado de calendarios.|

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que define un rectángulo cuyo tamaño es menor o igual que el rectángulo definido por el *parámetro lpRect.*

### <a name="remarks"></a>Observaciones

Este método calcula cuántos calendarios pueden caber en el rectángulo especificado por el *parámetro lpRect* y, a continuación, devuelve el rectángulo más pequeño que puede contener ese número de calendarios. En efecto, este método reduce el rectángulo especificado para ajustarse exactamente al número deseado de calendarios.

Este método envía el [mensaje MCM_SIZERECTTOMIN,](/windows/win32/Controls/mcm-sizerecttomin) que se describe en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl (clase)](../../mfc/reference/cdatetimectrl-class.md)
