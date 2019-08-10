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
ms.openlocfilehash: 1215247c194d75409c43d3fe1968ebab9ca71781
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916839"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (clase)

Encapsula la funcionalidad de un control de calendario mensual.

## <a name="syntax"></a>Sintaxis

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Construye un objeto `CMonthCalCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|Crea un control de calendario mensual y lo adjunta al `CMonthCalCtrl` objeto.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Recupera el ancho del borde del control de calendario mensual actual.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Recupera el número de calendarios mostrados en el control de calendario mensual actual.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Recupera información sobre el control de calendario mensual actual.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Recupera el identificador de calendario del control de calendario mensual actual.|
|[CMonthCalCtrl::GetColor](#getcolor)|Obtiene el color de un área especificada de un control de calendario mensual.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Recupera la vista que se muestra actualmente en el control de calendario mensual actual.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Recupera la hora del sistema indicada por la fecha seleccionada actualmente.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtiene el primer día de la semana que se va a mostrar en la columna situada más a la izquierda del calendario.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario mensual.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Recupera el ancho máximo de la cadena "Today" para el control de calendario mensual actual.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Recupera la tasa de desplazamiento para un control de calendario mensual.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Recupera información de fecha que representa los límites máximo y mínimo de la presentación de un control de calendario mensual.|
|[CMonthCalCtrl::GetRange](#getrange)|Recupera las fechas mínima y máxima actuales establecidas en un control de calendario mensual.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Recupera información de fecha que representa los límites superior e inferior del intervalo de fechas seleccionado actualmente por el usuario.|
|[CMonthCalCtrl::GetToday](#gettoday)|Recupera la información de fecha de la fecha especificada como "hoy" para un control de calendario mensual.|
|[CMonthCalCtrl::HitTest](#hittest)|Determina qué sección de un control de calendario mensual se encuentra en un punto determinado de la pantalla.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indica si la vista actual del control de calendario mensual actual es la vista de siglo.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indica si la vista actual del control de calendario mensual actual es la vista de la década.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indica si la vista actual del control de calendario mensual actual es la vista de mes.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Indica si la vista actual del control de calendario mensual actual es la vista de año.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Establece el ancho del borde del control de calendario mensual actual.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Establece el ancho predeterminado del borde del control de calendario mensual actual.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Establece el identificador de calendario del control de calendario mensual actual.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Establece el control de calendario mensual actual para mostrar la vista de siglo.|
|[CMonthCalCtrl::SetColor](#setcolor)|Establece el color de un área especificada de un control de calendario mensual.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Establece el control de calendario mensual actual para mostrar la vista especificada.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Establece la fecha seleccionada actualmente para un control de calendario mensual.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Establece la presentación de los días de un control de calendario mensual.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Establece el control de calendario mensual actual en la vista de década.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Establece el día de la semana que se va a mostrar en la columna situada más a la izquierda del calendario.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Establece el número máximo de días que se pueden seleccionar en un control de calendario mensual.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Establece la tasa de desplazamiento para un control de calendario mensual.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Establece el control de calendario mensual actual para mostrar la vista de mes.|
|[CMonthCalCtrl::SetRange](#setrange)|Establece las fechas mínima y máxima permitida para un control de calendario mensual.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Establece la selección de un control de calendario mensual en un intervalo de fechas determinado.|
|[CMonthCalCtrl::SetToday](#settoday)|Establece el control de calendario para el día actual.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Establece el control de calendario mensual actual en la vista de año.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Vuelve a dibujar el control de calendario mensual a su tamaño mínimo de un mes.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Para el control de calendario mensual actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.|

## <a name="remarks"></a>Comentarios

El control de calendario mensual proporciona al usuario una interfaz de calendario simple, desde la que el usuario puede seleccionar una fecha. El usuario puede cambiar la presentación de la siguiente manera:

- Desplazarse hacia atrás y hacia delante, desde el mes hasta el mes.

- Hacer clic en el texto hoy para mostrar el día actual (si no se usa el estilo MCS_NOTODAY).

- Selección de un mes o un año en un menú emergente.

Puede personalizar el control de calendario mensual aplicando una variedad de estilos al objeto al crearlo. Estos estilos se describen en [estilos de control de calendario mensual](/windows/desktop/Controls/month-calendar-control-styles) en el Windows SDK.

El control de calendario mensual puede mostrar más de un mes y puede indicar días especiales (como festivos) al poner en negrita la fecha.

Para obtener más información sobre el uso del control de calendario mensual, vea [usar CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdtctl. h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

Construye un objeto `CMonthCalCtrl`.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Comentarios

Debe llamar a `Create` después de construir el objeto.

##  <a name="create"></a>  CMonthCalCtrl::Create

Crea un control de calendario mensual y lo adjunta al `CMonthCalCtrl` objeto.

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
Especifica la combinación de estilos de Windows aplicada al control de calendario mensual. Vea [estilos de control de calendario mensual](/windows/desktop/Controls/month-calendar-control-styles) en el Windows SDK para obtener más información sobre los estilos.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) . Contiene la posición y el tamaño del control de calendario mensual.

*pt*<br/>
Referencia a una estructura de [punto](/previous-versions/dd162805\(v=vs.85\)) que identifica la ubicación del control de calendario mensual.

*pParentWnd*<br/>
Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control de calendario mensual. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control de calendario mensual.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cree un control de calendario mensual en dos pasos:

1. Llame a [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) para construir `CMonthCalCtrl` un objeto.

1. Llame a esta función miembro, que crea un control de calendario mensual y lo adjunta al `CMonthCalCtrl` objeto.

Cuando se llama `Create`a, se inicializan los controles comunes. La versión de `Create` a la que llama determina su tamaño:

- Para que MFC ajuste automáticamente el tamaño del control a un mes, llame a la invalidación que usa el parámetro *PT* .

- Para cambiar el tamaño del control, llame a la invalidación de esta función que usa el parámetro *Rect* .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

Recupera el ancho del borde del control de calendario mensual actual.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho del borde del control, en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder) , que se describe en el Windows SDK.

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

Recupera el número de calendarios mostrados en el control de calendario mensual actual.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de calendarios que se muestran actualmente en el control de calendario mensual. El número máximo permitido de calendarios es 12.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount) , que se describe en el Windows SDK.

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

Recupera información sobre el control de calendario mensual actual.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pmcGridInfo*|enuncia Puntero a una estructura [MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo) que recibe información sobre el control de calendario mensual actual. El autor de la llamada es responsable de la asignación e inicialización de esta estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetCalendarGridInfo` se usa el método para recuperar la fecha del calendario que se muestra en el control de calendario mensual actual.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

Recupera el identificador de calendario del control de calendario mensual actual.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Valor devuelto

Una de las constantes de [identificador de calendario](/windows/desktop/Intl/calendar-identifiers) .

### <a name="remarks"></a>Comentarios

Un identificador de calendario denota un calendario específico de la región, como los calendarios gregoriano (localizado), Japonés o Hijri. La aplicación puede usar un identificador de calendario que tenga varias funciones de compatibilidad de idioma.

Este método envía el mensaje [MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid) , que se describe en el Windows SDK.

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

Recupera el color de un área del control de calendario mensual especificado por *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parámetros

*nRegion*<br/>
Región del control de calendario mensual a partir del cual se recupera el color. Para obtener una lista de valores, vea el parámetro *nRegion* de [SetColor](#setcolor).

### <a name="return-value"></a>Valor devuelto

Un valor [COLORREF](/windows/desktop/gdi/colorref) que especifica el color asociado a la parte del control de calendario mensual, si es correcto. De lo contrario, esta función miembro devuelve-1.

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

Recupera la vista que se muestra actualmente en el control de calendario mensual actual.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Valor devuelto

Vista actual, que se indica mediante uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|MCMV_MONTH|Vista mensual|
|MCMV_YEAR|Vista anual|
|MCMV_DECADE|Vista de década|
|MCMV_CENTURY|Vista de siglo|

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se informa de qué vista del control de calendario mensual se muestra actualmente.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

Recupera la hora del sistema indicada por la fecha seleccionada actualmente.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) . Recibe la hora actual.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que recibirá la información de fecha seleccionada actualmente. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; otherwize 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel), tal y como se describe en el Windows SDK.

> [!NOTE]
>  Se produce un error en esta función miembro si se establece el estilo MCS_MULTISELECT.

En la implementación de MFC `GetCurSel`de, puede especificar el `COleDateTime` uso, el `CTime` uso o el uso `SYSTEMTIME` de una estructura.

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

Obtiene el primer día de la semana que se va a mostrar en la columna situada más a la izquierda del calendario.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parámetros

*pbLocal*<br/>
Un puntero a un valor BOOLEANO. Si el valor es distinto de cero, la configuración del control no coincide con la configuración del panel de control.

### <a name="return-value"></a>Valor devuelto

Valor entero que representa el primer día de la semana. Vea la **sección Comentarios** para obtener más información sobre lo que representan estos enteros.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek), tal y como se describe en el Windows SDK. Los días de la semana se representan como enteros, como se indica a continuación.

|Valor|Día de la semana|
|-----------|---------------------|
|0|Lunes|
|1|Martes|
|2|Miércoles|
|3|Jueves|
|4|Viernes|
|5|Sábado|
|6|Domingo|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek).

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario mensual.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que representa el número total de días que se pueden seleccionar para el control.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount), tal y como se describe en el Windows SDK. Utilice esta función miembro para los controles con el conjunto de estilos MCS_MULTISELECT.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount).

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

Recupera el ancho máximo de la cadena "Today" para el control de calendario mensual actual.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho de la cadena "Today", en píxeles.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetMaxTodayWidth` se muestra el método.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Comentarios

El usuario puede volver a la fecha actual haciendo clic en la cadena "hoy", que se muestra en la parte inferior del control de calendario mensual. La cadena "Today" incluye el texto de la etiqueta y el texto de la fecha.

Este método envía el mensaje [MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth) , que se describe en el Windows SDK.

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parámetros

*pRect*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibirá información del rectángulo delimitador. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, esta función miembro devuelve un `lpRect` valor distinto de cero y recibe la información de delimitación aplicable. Si no se realiza correctamente, la función miembro devuelve 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect), tal y como se describe en el Windows SDK.

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

Recupera la tasa de desplazamiento para un control de calendario mensual.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Valor devuelto

La tasa de desplazamiento para el control de calendario mensual. La tasa de desplazamiento es el número de meses que el control mueve su presentación cuando el usuario hace clic una vez en un botón de desplazamiento.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta), tal y como se describe en el Windows SDK.

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

Recupera información de fecha que representa los límites máximo y mínimo de la presentación de un control de calendario mensual.

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
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la fecha mínima permitida.

*refMaxRange*<br/>
Referencia a un `COleDateTime` objeto o `CTime` que contiene la fecha máxima permitida.

*pMinRange*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo inferior del intervalo.

*pMaxRange*<br/>
Puntero a una `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.

*dwFlags*<br/>
Valor que especifica el ámbito de los límites de intervalo que se van a recuperar. Este valor debe ser uno de los siguientes.

|Valor|Significado|
|-----------|-------------|
|GMR_DAYSTATE|Incluye los meses anteriores y finales del intervalo visible que solo se muestran parcialmente.|
|GMR_VISIBLE|Incluye solo los meses que se muestran por completo.|

### <a name="return-value"></a>Valor devuelto

Entero que representa el intervalo, en meses, que abarcan los dos límites indicados por *refMinRange* y *refMaxRange* en la primera y segunda versión, o *pMinRange* y *pMaxRange* en la tercera versión.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange), tal y como se describe en el Windows SDK. En la implementación de MFC `GetMonthRange`de, puede especificar `COleDateTime` el uso, `CTime` el uso o el `SYSTEMTIME` uso de una estructura.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl:: SetDayState](#setdaystate).

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

Recupera las fechas mínima y máxima actuales establecidas en un control de calendario mensual.

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
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo inferior del intervalo.

*pMaxRange*<br/>
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo superior del intervalo.

### <a name="return-value"></a>Valor devuelto

DWORD que puede ser cero (no se establecen límites) o una combinación de los siguientes valores que especifican la información de límite.

|Valor|Significado|
|-----------|-------------|
|GDTR_MAX|Se establece un límite máximo para el control; *pMaxRange* es válido y contiene la información de fecha aplicable.|
|GDTR_MIN|Se establece un límite mínimo para el control. *pMinRange* es válido y contiene la información de fecha aplicable.|

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange), tal y como se describe en el Windows SDK. En la implementación de MFC `GetRange`de, puede especificar el `COleDateTime` uso, el `CTime` uso o el uso `SYSTEMTIME` de una estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

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
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la fecha mínima permitida.

*refMaxRange*<br/>
Referencia a un `COleDateTime` objeto o `CTime` que contiene la fecha máxima permitida.

*pMinRange*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo inferior del intervalo.

*pMaxRange*<br/>
Puntero a una `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange), tal y como se describe en el Windows SDK. `GetSelRange`producirá un error si se aplica a un control de calendario mensual que no use el estilo MCS_MULTISELECT.

En la implementación de MFC `GetSelRange`de, puede especificar `COleDateTime` el uso, `CTime` el uso o el `SYSTEMTIME` uso de una estructura.

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

Recupera la información de fecha de la fecha especificada como "hoy" para un control de calendario mensual.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que indica el día actual.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que recibirá la información de fecha. Este parámetro debe ser una dirección válida y no puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday), tal y como se describe en el Windows SDK. En la implementación de MFC `GetToday`de, puede especificar el `COleDateTime` uso, el `CTime` uso o el uso `SYSTEMTIME` de una estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

Determina el control de calendario mensual que se encuentra en una posición especificada, si existe.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parámetros

*pMCHitTest*<br/>
Puntero a una estructura [MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo) que contiene puntos de prueba de posicionamiento para el control de calendario mensual.

### <a name="return-value"></a>Valor devuelto

Valor DWORD. Igual al miembro **uHit** de la `MCHITTESTINFO` estructura.

### <a name="remarks"></a>Comentarios

`HitTest`utiliza la `MCHITTESTINFO` estructura, que contiene información sobre la prueba de posicionamiento.

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

Indica si la vista actual del control de calendario mensual actual es la vista de siglo.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la vista actual es la vista de siglo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_CENTURY, este método devuelve TRUE.

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

Indica si la vista actual del control de calendario mensual actual es la vista de la década.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la vista actual es la vista de la década; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_DECADE, este método devuelve TRUE.

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

Indica si la vista actual del control de calendario mensual actual es la vista de mes.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la vista actual es la vista de mes; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_MONTH, este método devuelve TRUE.

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

Indica si la vista actual del control de calendario mensual actual es la vista de año.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la vista actual es la vista de año; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) , que se describe en el Windows SDK. Si ese mensaje devuelve MCMV_YEAR, este método devuelve TRUE.

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

Establece el ancho del borde del control de calendario mensual actual.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*cxyBorder*|de Ancho del borde, en píxeles.|

### <a name="remarks"></a>Comentarios

Si este método se ejecuta correctamente, el ancho del borde se establece en el parámetro *cxyBorder* . De lo contrario, el ancho del borde se restablece en el valor predeterminado especificado por el [tema](/windows/desktop/Controls/visual-styles-overview)actual, o bien, cero si no se usan los temas.

Este método envía el mensaje [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el ancho del borde del control de calendario mensual en ocho píxeles. Use el método [CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder) para determinar si este método se ejecutó correctamente.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

Establece el ancho predeterminado del borde del control de calendario mensual actual.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Comentarios

El ancho del borde se establece en el valor predeterminado especificado por el [tema](/windows/desktop/Controls/visual-styles-overview)actual, o bien, cero si no se usan los temas.

Este método envía el mensaje [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) , que se describe en el Windows SDK.

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

Establece el identificador de calendario del control de calendario mensual actual.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*calid*|de Una de las constantes de [identificador de calendario](/windows/desktop/Intl/calendar-identifiers) .|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un identificador de calendario especifica un calendario específico de la región, como los calendarios gregoriano (localizado), Japonés o Hijri. Use el `SetCalID` método para mostrar un calendario especificado por el parámetro *calid* si la configuración regional que contiene el calendario está instalada en el equipo.

Este método envía el mensaje [MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control de calendario mensual para mostrar el calendario de la era del Emperador japonés. El `SetCalID` método solo se realiza correctamente si ese calendario está instalado en el equipo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

Establece el control de calendario mensual actual para mostrar la vista de siglo.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa el método [CMonthCalCtrl:: SetCurrentView](#setcurrentview) para establecer la vista en `MCMV_CENTURY`, que representa la vista de siglo.

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

Establece el color de un área especificada de un control de calendario mensual.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*nRegion*<br/>
Valor entero que especifica el color de calendario mensual que se va a establecer. Este valor puede ser uno de los siguientes.

|Valor|Significado|
|-----------|-------------|
|MCSC_BACKGROUND|Color de fondo que se muestra entre meses.|
|MCSC_MONTHBK|Color de fondo que se muestra en el mes.|
|MCSC_TEXT|Color usado para mostrar el texto dentro de un mes.|
|MCSC_TITLEBK|Color de fondo que se muestra en el título del calendario.|
|MCSC_TITLETEXT|Color utilizado para mostrar texto en el título del calendario.|
|MCSC_TRAILINGTEXT|Color usado para mostrar el texto del encabezado y el final del día. Los días de encabezado y final son los días desde los meses anterior y siguiente que aparecen en el calendario actual.|

*ref*<br/>
Un valor de COLORREF para la nueva configuración de color para la parte especificada del control de calendario mensual.

### <a name="return-value"></a>Valor devuelto

Un valor de COLORREF que representa la configuración de color anterior para la parte especificada del control de calendario mensual, si se realiza correctamente. En caso contrario, este mensaje devuelve-1.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

Establece el control de calendario mensual actual para mostrar la vista especificada.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwNewView*|de Uno de los siguientes valores que especifica una vista mensual, anual, década u Century.<br /><br /> MCMV_MONTH: Vista mensual<br /><br /> MCMV_YEAR: Vista anual<br /><br /> MCMV_DECADE: Vista de década<br /><br /> MCMV_CENTURY: Vista de siglo|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview) , que se describe en el Windows SDK.

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

Establece la fecha seleccionada actualmente para un control de calendario mensual.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que indica el control de calendario mensual seleccionado actualmente.

*pDateTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha que se va a establecer como la selección actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel), tal y como se describe en el Windows SDK. En la implementación de MFC `SetCurSel`de, puede especificar el `COleDateTime` uso, el `CTime` uso o el uso `SYSTEMTIME` de una estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState

Establece la presentación de los días de un control de calendario mensual.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parámetros

*nMonths*<br/>
Valor que indica el número de elementos que hay en la matriz a la que apunta *pStates* .

*pStates*<br/>
Puntero a una matriz de valores de [MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate) que definen cómo se dibujará el control de calendario mensual cada día en la pantalla. El tipo de datos MONTHDAYSTATE es un campo de bits, donde cada bit (del 1 al 31) representa el estado de un día de un mes. Si un bit está activado, el día correspondiente se mostrará en negrita; en caso contrario, se mostrará sin énfasis.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

Establece el control de calendario mensual actual en la vista de década.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa el método [CMonthCalCtrl:: SetCurrentView](#setcurrentview) para establecer la vista en `MCMV_DECADE`, que representa la vista de la década.

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

Establece el día de la semana que se va a mostrar en la columna situada más a la izquierda del calendario.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parámetros

*iDay*<br/>
Valor entero que representa el día que se va a establecer como primer día de la semana. Este valor debe ser uno de los números de día. Vea [GetFirstDayOfWeek](#getfirstdayofweek) para obtener una descripción de los números de día.

*lpnOld*<br/>
Un puntero a un entero que indica el primer día de la semana establecido previamente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el primer día de la semana anterior se establece en un valor distinto del de LOCALE_IFIRSTDAYOFWEEK, que es el día indicado en la configuración del panel de control. De lo contrario, esta función devuelve 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

Establece el número máximo de días que se pueden seleccionar en un control de calendario mensual.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parámetros

*Nmáx.*<br/>
Valor que se establecerá para representar el número máximo de días seleccionables.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

Establece la tasa de desplazamiento para un control de calendario mensual.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parámetros

*iDelta*<br/>
Número de meses que se van a establecer como la tasa de desplazamiento del control. Si este valor es cero, la diferencia de mes se restablece en el valor predeterminado, que es el número de meses que se muestran en el control.

### <a name="return-value"></a>Valor devuelto

La tasa de desplazamiento anterior. Si la tasa de desplazamiento no se ha establecido previamente, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta), tal y como se describe en el Windows SDK.

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

Establece el control de calendario mensual actual para mostrar la vista de mes.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa el método [CMonthCalCtrl:: SetCurrentView](#setcurrentview) para establecer la vista en MCMV_MONTH, que representa la vista de mes.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_monthCalCtrl`la variable,, que se utiliza para tener acceso mediante programación al control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control de calendario mensual para mostrar las vistas mes, año, década y siglo.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

Establece las fechas mínima y máxima permitida para un control de calendario mensual.

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
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo inferior del intervalo.

*pMaxRange*<br/>
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o `SYSTEMTIME` una estructura que contiene la fecha en el extremo superior del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange), tal y como se describe en el Windows SDK. En la implementación de MFC `SetRange`de, puede especificar `COleDateTime` el uso, `CTime` el uso o el `SYSTEMTIME` uso de una estructura.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl:: GetRange](#getrange).

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

Establece la selección de un control de calendario mensual en un intervalo de fechas determinado.

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
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la fecha en el extremo inferior del intervalo.

*pMaxRange*<br/>
Un puntero a un `COleDateTime` objeto, un `CTime` objeto o `SYSTEMTIME` una estructura que contiene la fecha en el extremo superior del intervalo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange), tal y como se describe en el Windows SDK. En la implementación de MFC `SetSelRange`de, puede especificar `COleDateTime` el uso, `CTime` el uso o el `SYSTEMTIME` uso de una estructura.

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

Establece el control de calendario para el día actual.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parámetros

*refDateTime*<br/>
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene la fecha actual.

*pDateTime*<br/>
En la segunda versión, puntero a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la información de fecha actual. En la tercera versión, puntero a una estructura [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) que contiene la información de fecha actual.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMonthCalCtrl:: GetToday](#gettoday).

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

Establece el control de calendario mensual actual en la vista de año.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa el método [CMonthCalCtrl:: SetCurrentView](#setcurrentview) para establecer la vista en MCMV_YEAR, que representa la vista anual.

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

Muestra el control de calendario mensual al tamaño mínimo que muestra un mes.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parámetros

*bRepaint*<br/>
Especifica si se debe volver a dibujar el control. De forma predeterminada, es TRUE. Si es FALSE, no se produce ninguna repintado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control de calendario mensual tiene un tamaño mínimo; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Al `SizeMinReq` llamar a correctamente, se muestra el control de calendario mensual completo del calendario de un mes.

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

Para el control de calendario mensual actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*lpRect*|de Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que define un rectángulo que contiene el número deseado de calendarios.|

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que define un rectángulo cuyo tamaño es menor o igual que el rectángulo definido por el parámetro *lpRect* .

### <a name="remarks"></a>Comentarios

Este método calcula cuántos calendarios pueden caber en el rectángulo especificado por el parámetro *lpRect* y, a continuación, devuelve el rectángulo más pequeño que puede contener ese número de calendarios. En efecto, este método reduce el rectángulo especificado para ajustarse exactamente al número deseado de calendarios.

Este método envía el mensaje [MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin) , que se describe en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl (clase)](../../mfc/reference/cdatetimectrl-class.md)
