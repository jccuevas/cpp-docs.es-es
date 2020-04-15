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
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321915"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl (clase)

Encapsula la funcionalidad de un control selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Construye un objeto `CDateTimeCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Cierra el control de selector de fecha y hora actual.|
|[CDateTimeCtrl::Create](#create)|Crea el control selector de fecha y `CDateTimeCtrl` hora y lo adjunta al objeto.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Recupera información sobre el control de selector de fecha y hora actual.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Devuelve el tamaño ideal del control selector de fecha y hora necesario para mostrar la fecha u hora actual.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Recupera el color de una parte determinada del calendario del mes dentro del control de selector de fecha y hora.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Recupera el `CMonthCalCtrl` objeto asociado con el control selector de fecha y hora.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Recupera la fuente utilizada actualmente por el control de calendario de mes secundario del control de selector de fecha y hora.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Obtiene el estilo del control de selector de fecha y hora actual.|
|[CDateTimeCtrl::GetRange](#getrange)|Recupera las horas mínimas y máximas actuales permitidas del sistema para un control de selector de fecha y hora.|
|[CDateTimeCtrl::GetTime](#gettime)|Recupera la hora seleccionada actualmente de un control de selector `SYSTEMTIME` de fecha y hora y lo coloca en una estructura especificada.|
|[CDateTimeCtrl::SetFormat](#setformat)|Establece la visualización de un control selector de fecha y hora de acuerdo con una cadena de formato determinada.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Establece el color de una parte determinada del calendario del mes dentro de un control de selector de fecha y hora.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Establece la fuente que usará el control de calendario de mes secundario del control de selector de fecha y hora.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Establece el estilo del control de selector de fecha y hora actual.|
|[CDateTimeCtrl::SetRange](#setrange)|Establece las horas mínimas y máximas permitidas del sistema para un control de selector de fecha y hora.|
|[CDateTimeCtrl::SetTime](#settime)|Establece la hora en un control de selector de fecha y hora.|

## <a name="remarks"></a>Observaciones

El control de selector de fecha y hora (control DTP) proporciona una interfaz sencilla para intercambiar información de fecha y hora con un usuario. Esta interfaz contiene campos, cada uno de los cuales muestra una parte de la información de fecha y hora almacenada en el control. El usuario puede cambiar la información almacenada en el control cambiando el contenido de la cadena en un campo determinado. El usuario puede moverse de un campo a otro con el ratón o el teclado.

Puede personalizar el control de selector de fecha y hora aplicando una variedad de estilos al objeto al crearlo. Consulte [Estilos](/windows/win32/Controls/date-and-time-picker-control-styles) de control de selector de fecha y hora en el Windows SDK para obtener más información acerca de los estilos específicos del control de selector de fecha y hora. Puede establecer el formato de visualización del control DTP mediante estilos de formato. Estos estilos de formato se describen en "Estilos de formato" en el tema de Windows SDK [Estilos](/windows/win32/Controls/date-and-time-picker-control-styles)de control de selector de fecha y hora .

El control selector de fecha y hora también usa notificaciones y devoluciones de llamada, que se describen en Uso de [CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl

Construye un objeto `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal

Cierra el control de selector de fecha y hora actual.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje DTM_CLOSEMONTHCAL,](/windows/win32/Controls/dtm-closemonthcal) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cierra el calendario desplegable para el control de selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Create

Crea el control selector de fecha y `CDateTimeCtrl` hora y lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de control de fecha y hora. Consulta [Estilos](/windows/win32/Controls/date-and-time-picker-control-styles) de control de selector de fecha y hora en el Windows SDK para obtener más información sobre los estilos de selector de fecha y hora.

*Rect*<br/>
Una referencia a una estructura [RECT,](/previous-versions/dd162897\(v=vs.85\)) que es la posición y el tamaño del control de selector de fecha y hora.

*pParentWnd*<br/>
Puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control selector de fecha y hora. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control del selector de fecha y hora.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la creación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

##### <a name="to-create-a-date-and-time-picker-control"></a>Para crear un control de selector de fecha y hora

1. Llame a [CDateTimeCtrl](#cdatetimectrl) para construir un `CDateTimeCtrl` objeto.

1. Llame a esta función miembro, que crea el control `CDateTimeCtrl` de selector de fecha y hora de Windows y lo adjunta al objeto.

Cuando se `Create`llama a , se inicializan los controles comunes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo

Recupera información sobre el control de selector de fecha y hora actual.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDateTimePickerInfo*|[fuera] Puntero a una estructura [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) que recibe una descripción del control de selector de fecha y hora actual.<br /><br /> El autor de la llamada es responsable de asignar esta estructura. Sin embargo, este método inicializa el *cbSize* miembro de la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje DTM_GETDATETIMEPICKERINFO,](/windows/win32/Controls/dtm-getdatetimepickerinfo) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se indica si recupera correctamente información sobre el control de selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor

Recupera el color de una parte determinada del calendario del mes dentro del control de selector de fecha y hora.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
Valor **int** que especifica el área de color del calendario del mes que se va a recuperar. Para obtener una lista de valores, vea el parámetro *iColor* para [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valor devuelto

Un COLORREF valor que representa la configuración de color para la parte especificada del control de calendario de mes si se realiza correctamente. La función devuelve -1 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/dtm-getmccolor)Win32 DTM_GETMCCOLOR , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl

Recupera el `CMonthCalCtrl` objeto asociado con el control selector de fecha y hora.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) objeto, o NULL si no se realiza correctamente o si la ventana no está visible.

### <a name="remarks"></a>Observaciones

Los controles del selector de fecha y hora crean un control de calendario de mes secundario cuando el usuario hace clic en la flecha desplegable. Cuando `CMonthCalCtrl` el objeto ya no es necesario, se destruye, por lo que la aplicación no debe confiar en almacenar el objeto que representa el calendario de mes secundario del control selector de fecha y hora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont

Obtiene la fuente utilizada actualmente por el control de calendario de mes del control selector de fecha y hora.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto, o NULL si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El `CFont` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle

Obtiene el estilo del control de calendario de mes desplegable que está asociado con el control de selector de fecha y hora actual.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valor devuelto

El estilo del control de calendario de mes desplegable, que es una combinación bit a bit (OR) de estilos de control de selector de fecha y hora. Para obtener más información, consulte Estilos de control de calendario de [mes](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje DTM_GETMCSTYLE,](/windows/win32/Controls/dtm-getmcstyle) que se describe en el Windows SDK.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange

Recupera las horas mínimas y máximas actuales permitidas del sistema para un control de selector de fecha y hora.

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
Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto `CDateTimeCtrl` que contiene la primera vez permitido en el objeto.

*pMaxRange*<br/>
Puntero a `COleDateTime` un objeto `CTime` o un objeto que `CDateTimeCtrl` contiene la última hora permitida en el objeto.

### <a name="return-value"></a>Valor devuelto

Valor DWORD que contiene indicadores que indican qué intervalos se establecen. Si

`return value & GDTR_MAX` == 0

entonces el segundo parámetro es válido. Del mismo modo, si

`return value & GDTR_MIN` == 0

entonces el primer parámetro es válido.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange), como se describe en el Windows SDK. En la implementación de MFC, puede especificar cualquiera `COleDateTime` o `CTime` usos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime

Recupera la hora seleccionada actualmente de un control de selector `SYSTEMTIME` de fecha y hora y lo coloca en una estructura especificada.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
En la primera versión, una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda versión, una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de tiempo del sistema.

*pTimeDest*<br/>
Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera versión, distinto de cero `COleDateTime` si la hora se escribe correctamente en el objeto; de lo contrario 0. En la segunda y tercera versiones, un valor DWORD igual al miembro *dwFlag* establecido en la estructura [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Consulte la sección **Comentarios** a continuación para obtener más información.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime), como se describe en el Windows SDK. En la implementación MFC `COleDateTime` de `CTime` , puede usar `SYSTEMTIME` o clases, o puede usar una estructura, para almacenar la información de `GetTime`tiempo.

El valor devuelto DWORD en las versiones segunda y tercera, anteriormente, indica si el control selector de fecha y hora se establece en el estado "sin fecha", como se indica en el miembro de estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *dwFlags*. Si el valor devuelto es igual a GDT_NONE, el control se establece en el estado "sin fecha" y usa el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema se almacena correctamente en la ubicación de destino.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize

Devuelve el tamaño ideal del control selector de fecha y hora necesario para mostrar la fecha u hora actual.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*psize*|[fuera] Puntero a una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) que contiene el tamaño ideal para el control.|

### <a name="return-value"></a>Valor devuelto

El valor devuelto siempre es TRUE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje DTM_GETIDEALSIZE,](/windows/win32/Controls/dtm-getidealsize) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera el tamaño ideal para mostrar el control de selector de fecha y hora.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::SetFormat

Establece la visualización de un control selector de fecha y hora de acuerdo con una cadena de formato determinada.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parámetros

*pstrFormat*<br/>
Puntero a una cadena de formato terminada en cero que define la visualización deseada. Establecer este parámetro en NULL restablecerá el control a la cadena de formato predeterminada para el estilo actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

> [!NOTE]
> La entrada del usuario no determina el éxito o el error para esta llamada.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)de mensaje de Win32 , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor

Establece el color de una parte determinada del calendario del mes dentro de un control de selector de fecha y hora.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
**int** valor especificando qué área del control de calendario de mes para establecer. Este valor puede ser uno de los siguientes.

|Value|Significado|
|-----------|-------------|
|MCSC_BACKGROUND|Establezca el color de fondo que se muestra entre meses.|
|MCSC_MONTHBK|Establezca el color de fondo que se muestra en el plazo de un mes.|
|MCSC_TEXT|Establezca el color utilizado para mostrar texto en el plazo de un mes.|
|MCSC_TITLEBK|Establezca el color de fondo que se muestra en el título del calendario.|
|MCSC_TITLETEXT|Establezca el color utilizado para mostrar texto dentro del título del calendario.|
|MCSC_TRAILINGTEXT|Establezca el color utilizado para mostrar el encabezado y el texto del día final. Los días de cabecera y de trailing son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|

*ref*<br/>
Un valor COLORREF que representa el color que se establecerá para el área especificada del calendario del mes.

### <a name="return-value"></a>Valor devuelto

Un COLORREF valor que representa la configuración de color anterior para la parte especificada del control de calendario de mes si se realiza correctamente. De lo contrario, el mensaje devuelve -1.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/dtm-setmccolor)Win32 DTM_SETMCCOLOR , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont

Establece la fuente que usará el control de calendario de mes secundario del control de selector de fecha y hora.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Controle la fuente que se establecerá.

*bRedraw*<br/>
Especifica si el control se debe volver a dibujar inmediatamente al establecer la fuente. Establecer este parámetro en TRUE hace que el control se vuelva a dibujar.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/dtm-setmcfont)Win32 DTM_SETMCFONT , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Si usa este código, querrá crear un miembro `CDialog`de la clase derivada `CFont`denominada *m_MonthFont* de tipo .

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle

Establece el estilo del control de calendario de mes desplegable asociado al control de selector de fecha y hora actual.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[en] Un nuevo estilo de control de calendario de mes, que es una combinación bit a bit (OR) de estilos de control de calendario de mes. Para obtener más información, consulte Estilos de control de calendario de [mes](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Valor devuelto

El estilo anterior del control de calendario del mes desplegable.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje DTM_SETMCSTYLE,](/windows/win32/Controls/dtm-setmcstyle) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_dateTimeCtrl*, que se usa para tener acceso mediante programación al control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el control selector de fecha y hora para mostrar los números de semana, los nombres abreviados de días de la semana y ningún indicador de hoy.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange

Establece las horas mínimas y máximas permitidas del sistema para un control de selector de fecha y hora.

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
Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto `CDateTimeCtrl` que contiene la primera vez permitido en el objeto.

*pMaxRange*<br/>
Puntero a `COleDateTime` un objeto `CTime` o un objeto que `CDateTimeCtrl` contiene la última hora permitida en el objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/dtm-setrange)Win32 DTM_SETRANGE , como se describe en el Windows SDK. En la implementación de MFC, puede especificar cualquiera `COleDateTime` o `CTime` usos. Si `COleDateTime` el objeto tiene un estado NULL, se quitará el intervalo. Si `CTime` el puntero `COleDateTime` o el puntero es NULL, se quitará el intervalo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl::GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime

Establece la hora en un control de selector de fecha y hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene el a la que se establecerá el control.

*pTimeNew*<br/>
En la segunda versión anterior, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control. En la tercera versión anterior, un puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime), como se describe en el Windows SDK. En la implementación MFC de `COleDateTime` `CTime` , puede usar las `SYSTEMTIME` clases o, o puede usar una estructura, para establecer la información de `SetTime`tiempo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl (clase)](../../mfc/reference/cmonthcalctrl-class.md)
