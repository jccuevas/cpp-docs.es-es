---
title: CDateTimeCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866939"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl (clase)

Encapsula la funcionalidad de un control selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDateTimeCtrl:: CDateTimeCtrl](#cdatetimectrl)|Construye un objeto `CDateTimeCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDateTimeCtrl:: CloseMonthCal](#closemonthcal)|Cierra el control de selector de fecha y hora actual.|
|[CDateTimeCtrl:: Create](#create)|Crea el control de selector de fecha y hora y lo adjunta al objeto `CDateTimeCtrl`.|
|[CDateTimeCtrl:: GetDateTimePickerInfo](#getdatetimepickerinfo)|Recupera información sobre el control de selector de fecha y hora actual.|
|[CDateTimeCtrl:: GetIdealSize](#getidealsize)|Devuelve el tamaño ideal del control selector de fecha y hora necesario para mostrar la fecha u hora actual.|
|[CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor)|Recupera el color para una parte determinada del calendario mensual dentro del control selector de fecha y hora.|
|[CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Recupera el objeto de `CMonthCalCtrl` asociado al control selector de fecha y hora.|
|[CDateTimeCtrl:: GetMonthCalFont](#getmonthcalfont)|Recupera la fuente utilizada actualmente por el control de calendario mensual del control de fecha y hora.|
|[CDateTimeCtrl:: GetMonthCalStyle](#getmonthcalstyle)|Obtiene el estilo del control selector de fecha y hora actual.|
|[CDateTimeCtrl:: GetRange](#getrange)|Recupera las horas de sistema mínimas y máximas permitidas para un control selector de fecha y hora.|
|[CDateTimeCtrl:: GetTime](#gettime)|Recupera la hora actualmente seleccionada de un control de selector de fecha y hora y la coloca en una estructura de `SYSTEMTIME` especificada.|
|[CDateTimeCtrl:: SetFormat](#setformat)|Establece la presentación de un control selector de fecha y hora de acuerdo con una cadena de formato determinada.|
|[CDateTimeCtrl:: SetMonthCalColor](#setmonthcalcolor)|Establece el color de una parte determinada del calendario mensual dentro de un control selector de fecha y hora.|
|[CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Establece la fuente que va a usar el control de calendario mensual del control de fecha y hora.|
|[CDateTimeCtrl:: SetMonthCalStyle](#setmonthcalstyle)|Establece el estilo del control selector de fecha y hora actual.|
|[CDateTimeCtrl:: SetRange](#setrange)|Establece las horas mínimas y máximas permitidas para un control selector de fecha y hora.|
|[CDateTimeCtrl:: SetTime](#settime)|Establece la hora en un control de selector de fecha y hora.|

## <a name="remarks"></a>Observaciones

El control selector de fecha y hora (control de DTP) proporciona una interfaz simple para intercambiar información de fecha y hora con un usuario. Esta interfaz contiene campos, cada uno de los cuales muestra una parte de la información de fecha y hora almacenada en el control. El usuario puede cambiar la información almacenada en el control cambiando el contenido de la cadena en un campo determinado. El usuario puede pasar de un campo a un campo mediante el mouse o el teclado.

Puede personalizar el control de selector de fecha y hora aplicando una variedad de estilos al objeto al crearlo. Vea [estilos de control de selector de fecha y hora](/windows/win32/Controls/date-and-time-picker-control-styles) en el Windows SDK para obtener más información sobre los estilos específicos del control selector de fecha y hora. Puede establecer el formato de presentación del control de DTP mediante los estilos de formato. Estos estilos de formato se describen en "estilos de formato" en los [estilos de control de selector de fecha y hora](/windows/win32/Controls/date-and-time-picker-control-styles)de Windows SDK tema.

El control selector de fecha y hora también utiliza notificaciones y devoluciones de llamada, que se describen en [uso de CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdtctl. h

##  <a name="cdatetimectrl"></a>CDateTimeCtrl:: CDateTimeCtrl

Construye un objeto `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>CDateTimeCtrl:: CloseMonthCal

Cierra el control de selector de fecha y hora actual.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cierra el calendario desplegable para el control selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>CDateTimeCtrl:: Create

Crea el control de selector de fecha y hora y lo adjunta al objeto `CDateTimeCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de control de fecha y hora. Para obtener más información acerca de los estilos de selector de fecha y hora, consulte [estilos de control del selector de fecha y hora](/windows/win32/Controls/date-and-time-picker-control-styles) en el Windows SDK.

*Rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) , que es la posición y el tamaño del control selector de fecha y hora.

*pParentWnd*<br/>
Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control de selector de fecha y hora. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control del selector de fecha y hora.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la creación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

##### <a name="to-create-a-date-and-time-picker-control"></a>Para crear un control de selector de fecha y hora

1. Llame a [CDateTimeCtrl](#cdatetimectrl) para construir un objeto de `CDateTimeCtrl`.

1. Llame a esta función miembro, que crea el control selector de fecha y hora de Windows y lo adjunta al objeto `CDateTimeCtrl`.

Cuando se llama a `Create`, se inicializan los controles comunes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl:: GetDateTimePickerInfo

Recupera información sobre el control de selector de fecha y hora actual.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDateTimePickerInfo*|enuncia Puntero a una estructura [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) que recibe una descripción del control de selector de fecha y hora actual.<br /><br /> El autor de la llamada es responsable de la asignación de esta estructura. Sin embargo, este método inicializa el miembro *cbSize* de la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se indica si se recupera correctamente información sobre el control selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>CDateTimeCtrl:: GetMonthCalColor

Recupera el color para una parte determinada del calendario mensual dentro del control selector de fecha y hora.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
Valor **int** que especifica el área de color del calendario mensual que se va a recuperar. Para obtener una lista de valores, vea el parámetro *iColor* para [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valor devuelto

Un valor de COLORREF que representa la configuración de color para la parte especificada del control de calendario mensual si se realiza correctamente. La función devuelve-1 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>CDateTimeCtrl:: GetMonthCalCtrl

Recupera el objeto de `CMonthCalCtrl` asociado al control selector de fecha y hora.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) , o null si no se realiza correctamente o si la ventana no está visible.

### <a name="remarks"></a>Observaciones

Los controles de selector de fecha y hora crean un control de calendario mensual secundario cuando el usuario hace clic en la flecha de lista desplegable. Cuando el objeto de `CMonthCalCtrl` ya no es necesario, se destruye, por lo que la aplicación no debe basarse en almacenar el objeto que representa el calendario mensual del control selector de fecha y hora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>CDateTimeCtrl:: GetMonthCalFont

Obtiene la fuente utilizada actualmente por el control de calendario mensual del control de fecha y hora.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [Cfont (](../../mfc/reference/cfont-class.md) o null si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El `CFont` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

##  <a name="getmonthcalstyle"></a>CDateTimeCtrl:: GetMonthCalStyle

Obtiene el estilo del control de calendario del mes desplegable que está asociado al control de selector de fecha y hora actual.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Estilo del control de calendario del mes desplegable, que es una combinación bit a bit (o) de estilos de control de selector de fecha y hora. Para obtener más información, vea [estilos de control de calendario mensual](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) , que se describe en el Windows SDK.

##  <a name="getrange"></a>CDateTimeCtrl:: GetRange

Recupera las horas de sistema mínimas y máximas permitidas para un control selector de fecha y hora.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parámetros

*pMinRange*<br/>
Un puntero a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la hora más temprana permitida en el objeto `CDateTimeCtrl`.

*pMaxRange*<br/>
Un puntero a un objeto `COleDateTime` o un objeto `CTime` que contiene la última hora permitida en el objeto `CDateTimeCtrl`.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene marcas que indican qué rangos se han establecido. Si

`return value & GDTR_MAX` == 0

después, el segundo parámetro es válido. De forma similar, si

`return value & GDTR_MIN` == 0

después, el primer parámetro es válido.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)de mensajes de Win32, como se describe en el Windows SDK. En la implementación de MFC, puede especificar los usos `COleDateTime` o `CTime`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>CDateTimeCtrl:: GetTime

Recupera la hora actualmente seleccionada de un control de selector de fecha y hora y la coloca en una estructura de `SYSTEMTIME` especificada.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
En la primera versión, se trata de una referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que recibirá la información de hora del sistema. En la segunda versión, referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que recibirá la información de hora del sistema.

*pTimeDest*<br/>
Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera versión, es distinto de cero si la hora se escribe correctamente en el objeto `COleDateTime`; de lo contrario, es 0. En la segunda y tercera versiones, un valor DWORD igual al miembro *dwFlag* establecido en la estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) . Vea la sección **comentarios** que aparece a continuación para obtener más información.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)de mensajes de Win32, como se describe en el Windows SDK. En la implementación de MFC de `GetTime`, puede usar `COleDateTime` o `CTime` clases, o bien, puede usar una estructura `SYSTEMTIME` para almacenar la información de hora.

El valor devuelto DWORD en la segunda y tercera versión, arriba, indica si el control de selector de fecha y hora está establecido en el estado "sin fecha", como se indica en el miembro de estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *dwFlags*. Si el valor devuelto es igual a GDT_NONE, el control se establece en el estado "sin fecha" y usa el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema se almacena correctamente en la ubicación de destino.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>CDateTimeCtrl:: GetIdealSize

Devuelve el tamaño ideal del control selector de fecha y hora necesario para mostrar la fecha u hora actual.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*psize*|enuncia Puntero a una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) que contiene el tamaño ideal para el control.|

### <a name="return-value"></a>Valor devuelto

El valor devuelto siempre es TRUE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el tamaño ideal para mostrar el control de selector de fecha y hora.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>CDateTimeCtrl:: SetFormat

Establece la presentación de un control selector de fecha y hora de acuerdo con una cadena de formato determinada.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parámetros

*pstrFormat*<br/>
Puntero a una cadena de formato terminada en cero que define la presentación deseada. Si se establece este parámetro en NULL, se restablecerá el control en la cadena de formato predeterminada para el estilo actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

> [!NOTE]
>  La entrada del usuario no determina si la llamada se ha realizado correctamente o no.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>CDateTimeCtrl:: SetMonthCalColor

Establece el color de una parte determinada del calendario mensual dentro de un control selector de fecha y hora.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
valor **int** que especifica el área del control de calendario mensual que se va a establecer. Este valor puede ser uno de los siguientes.

|Value|Significado|
|-----------|-------------|
|MCSC_BACKGROUND|Establecer el color de fondo que se muestra entre meses.|
|MCSC_MONTHBK|Establece el color de fondo que se muestra en un mes.|
|MCSC_TEXT|Establece el color usado para mostrar el texto dentro de un mes.|
|MCSC_TITLEBK|Establezca el color de fondo que se muestra en el título del calendario.|
|MCSC_TITLETEXT|Establece el color utilizado para mostrar texto en el título del calendario.|
|MCSC_TRAILINGTEXT|Establezca el color usado para mostrar el texto del encabezado y del día final. Los días de encabezado y final son los días desde los meses anterior y siguiente que aparecen en el calendario actual.|

*ref*<br/>
Un valor COLORREF que representa el color que se establecerá para el área especificada del calendario mensual.

### <a name="return-value"></a>Valor devuelto

Un valor COLORREF que representa la configuración de color anterior para la parte especificada del control de calendario mensual si se realiza correctamente. De lo contrario, el mensaje devuelve-1.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>CDateTimeCtrl:: SetMonthCalFont

Establece la fuente que va a usar el control de calendario mensual del control de fecha y hora.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Identificador de la fuente que se va a establecer.

*bRedraw*<br/>
Especifica si el control debe volver a dibujarse inmediatamente después de establecer la fuente. Establecer este parámetro en TRUE hace que el control se vuelva a dibujar.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Si usa este código, querrá crear un miembro de la clase derivada de `CDialog`denominada *m_MonthFont* de tipo `CFont`.

##  <a name="setmonthcalstyle"></a>CDateTimeCtrl:: SetMonthCalStyle

Establece el estilo del control de calendario del mes desplegable que está asociado al control de selector de fecha y hora actual.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|de Nuevo estilo de control de calendario mensual, que es una combinación bit a bit (o) de estilos de control de calendario mensual. Para obtener más información, vea [estilos de control de calendario mensual](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Valor devuelto

Estilo anterior del control de calendario del mes desplegable.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control selector de fecha y hora para mostrar los números de semana, los nombres abreviados de los días de la semana y el indicador no hoy.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>CDateTimeCtrl:: SetRange

Establece las horas mínimas y máximas permitidas para un control selector de fecha y hora.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parámetros

*pMinRange*<br/>
Un puntero a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la hora más temprana permitida en el objeto `CDateTimeCtrl`.

*pMaxRange*<br/>
Un puntero a un objeto `COleDateTime` o un objeto `CTime` que contiene la última hora permitida en el objeto `CDateTimeCtrl`.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)de mensajes de Win32, como se describe en el Windows SDK. En la implementación de MFC, puede especificar los usos `COleDateTime` o `CTime`. Si el objeto `COleDateTime` tiene un estado NULL, se quitará el intervalo. Si el puntero de `CTime` o el puntero de `COleDateTime` es NULL, se quitará el intervalo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl:: GetRange](#getrange).

##  <a name="settime"></a>CDateTimeCtrl:: SetTime

Establece la hora en un control de selector de fecha y hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
Referencia a un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene el objeto en el que se establecerá el control.

*pTimeNew*<br/>
En la segunda versión anterior, puntero a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la hora a la que se establecerá el control. En la tercera versión anterior, puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)de mensajes de Win32, como se describe en el Windows SDK. En la implementación de MFC de `SetTime`, puede usar las clases `COleDateTime` o `CTime`, o puede usar una estructura `SYSTEMTIME` para establecer la información de hora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl (clase)](../../mfc/reference/cmonthcalctrl-class.md)
