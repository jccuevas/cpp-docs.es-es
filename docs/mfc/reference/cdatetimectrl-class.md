---
title: CDateTimeCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57e2b990e8fddbcb81d942cb7327ed8b9d448e6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420249"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl (clase)

Encapsula la funcionalidad de un control selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Construye un objeto `CDateTimeCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Cierra el control de selector de fecha y hora actual.|
|[CDateTimeCtrl::Create](#create)|Crea el control de selector de fecha y hora y la conecta a la `CDateTimeCtrl` objeto.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Recupera información sobre el control de selector de fecha y hora actual.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Devuelve el tamaño ideal de control de selector de fecha y hora en que se requiere para mostrar la fecha actual o la hora.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Recupera el color de una parte determinada del calendario del mes en el control de selector de fecha y hora.|
|[CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Recupera el `CMonthCalCtrl` objeto asociado con el control de selector de fecha y hora.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Recupera la fuente utilizada actualmente por la fecha y el control de calendario mensual del control de selector de tiempo secundarias.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Obtiene el estilo del control de selector de fecha y hora actual.|
|[CDateTimeCtrl::GetRange](#getrange)|Recupera actual mínimo y máximo permitido de tiempos del sistema para un control de selector de fecha y hora.|
|[CDateTimeCtrl::GetTime](#gettime)|Recupera el tiempo seleccionado actualmente de un control de selector de fecha y hora y lo coloca en un determinado `SYSTEMTIME` estructura.|
|[CDateTimeCtrl:: SetFormat](#setformat)|Establece la visualización de un control de selector de fecha y hora con arreglo a una cadena de formato especificado.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Establece el color de una parte determinada del calendario mensual dentro de un control de selector de fecha y hora.|
|[CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Establece la fuente que utilizará el control de calendario mensual de fecha y hora selector del control secundario.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Establece el estilo del control de selector de fecha y hora actual.|
|[CDateTimeCtrl::SetRange](#setrange)|Establece las horas de sistema permitido mínimo y máximo para un control de selector de fecha y hora.|
|[CDateTimeCtrl::SetTime](#settime)|Establece el tiempo en un control de selector de fecha y hora.|

## <a name="remarks"></a>Comentarios

El control de selector de fecha y hora (control de DTP) proporciona una interfaz sencilla para intercambiar información de fecha y hora con un usuario. Esta interfaz contiene campos, cada uno de los cuales muestra una parte de la información de fecha y hora almacenada en el control. El usuario puede cambiar la información almacenada en el control cambiando el contenido de la cadena en un campo determinado. El usuario puede mover de un campo a otro utilizando el mouse o el teclado.

Puede personalizar el control de selector de fecha y hora mediante la aplicación de una variedad de estilos para el objeto al crearlo. Consulte [estilos de fecha y hora selector Control](/windows/desktop/Controls/date-and-time-picker-control-styles) en el SDK de Windows para obtener más información sobre los estilos específicos para el control de selector de fecha y hora. Puede establecer el formato de presentación del control DTP mediante estilos de formato. Estos estilos de formato se describen en "Estilos de formato" en el tema del SDK de Windows [estilos de fecha y hora selector Control](/windows/desktop/Controls/date-and-time-picker-control-styles).

El control de selector de fecha y hora también usa las notificaciones y las devoluciones de llamada, que se describen en [usar CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

Construye un objeto `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

Cierra el control de selector de fecha y hora actual.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Comentarios

Este método envía el [DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_dateTimeCtrl*, que se usa para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cierra el calendario desplegable para el control de selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

Crea el control de selector de fecha y hora y la conecta a la `CDateTimeCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de control de tiempo fecha. Consulte [estilos de fecha y hora selector Control](/windows/desktop/Controls/date-and-time-picker-control-styles) en el SDK de Windows para obtener más información sobre los estilos de selector de fecha y hora.

*Rect*<br/>
Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que es la posición y el tamaño del control de selector de fecha y hora.

*pParentWnd*<br/>
Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control de selector de fecha y hora. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control de. fecha y hora selector del control

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se creó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

##### <a name="to-create-a-date-and-time-picker-control"></a>Para crear un control de selector de fecha y hora

1. Llame a [CDateTimeCtrl](#cdatetimectrl) para construir un `CDateTimeCtrl` objeto.

1. Llame a esta función miembro, que crea el control de selector de fecha y hora de Windows y lo adjunta a la `CDateTimeCtrl` objeto.

Cuando se llama a `Create`, se inicializan los controles comunes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

Recupera información sobre el control de selector de fecha y hora actual.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out] Un puntero a un [DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo) estructura que recibe una descripción del control de selector de fecha y hora actual.<br /><br /> El llamador es responsable de asignar esta estructura. Sin embargo, este método inicializa la *cbSize* miembro de la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_dateTimeCtrl*, que se usa para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se indica si recupera correctamente información sobre el control de selector de fecha y hora actual.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

Recupera el color de una parte determinada del calendario del mes en el control de selector de fecha y hora.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
Un **int** valor que especifica qué área de color del calendario de mes para recuperar. Para obtener una lista de valores, vea el *iColor* parámetro [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valor devuelto

Un valor COLORREF que representa la configuración de color de la parte especificada del control de calendario mensual si se realiza correctamente. La función devuelve -1 si no lo consigue.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl:: GetMonthCalCtrl

Recupera el `CMonthCalCtrl` objeto asociado con el control de selector de fecha y hora.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) de objeto, o NULL si no lo consigue, o si la ventana no está visible.

### <a name="remarks"></a>Comentarios

Controles de selector de fecha y hora en crean un control de calendario mensual secundario cuando el usuario hace clic en la flecha de lista desplegable. Cuando el `CMonthCalCtrl` objeto ya no es necesario, se destruye, por lo que la aplicación no debe confiar en almacenar el objeto que representa el calendario mensual de fecha hora selector del control secundario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

Obtiene la fuente utilizada actualmente por la fecha y el control de calendario mensual del control de selector de hora.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto, o NULL si no lo consigue.

### <a name="remarks"></a>Comentarios

La `CFont` objeto al que señala el valor devuelto es un objeto temporal y se destruyen durante la próxima vez que el procesamiento inactivo.

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

Obtiene el estilo del control de calendario mensual de la lista desplegable que está asociado con el control de selector de fecha y hora actual.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valor devuelto

El estilo del control de calendario mensual de la lista desplegable, que es una combinación bit a bit (o) de los estilos de control de selector de fecha y hora. Para obtener más información, consulte [estilos de Control de calendario de mes](/windows/desktop/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Comentarios

Este método envía el [DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle) mensaje, que se describe en el SDK de Windows.

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

Recupera actual mínimo y máximo permitido de tiempos del sistema para un control de selector de fecha y hora.

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
Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora más temprana permitida en el `CDateTimeCtrl` objeto.

*pMaxRange*<br/>
Un puntero a un `COleDateTime` objeto o un `CTime` objeto que contiene la hora más reciente permitida en el `CDateTimeCtrl` objeto.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene las marcas que indican qué intervalos se establecen. Si

`return value & GDTR_MAX` == 0

a continuación, el segundo parámetro es válido. De forma similar, si

`return value & GDTR_MIN` == 0

a continuación, el primer parámetro es válido.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange), tal y como se describe en el SDK de Windows. En la implementación de MFC, puede especificar `COleDateTime` o `CTime` usos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

Recupera el tiempo seleccionado actualmente de un control de selector de fecha y hora y lo coloca en un determinado `SYSTEMTIME` estructura.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
En la primera versión, una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda versión, una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de hora del sistema.

*pTimeDest*<br/>
Un puntero a la [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) estructura para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera versión, distinto de cero si se ha escrito correctamente la hora a la `COleDateTime` objeto; en caso contrario, 0. En las versiones de la segunda y terceros, un valor DWORD de valor igual a la *dwFlag* miembro establecido el [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) estructura. Consulte la **comentarios** sección para obtener más información.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime), tal y como se describe en el SDK de Windows. En la implementación de MFC de `GetTime`, puede usar `COleDateTime` o `CTime` clases, o bien puede usar un `SYSTEMTIME` estructura para almacenar la información de hora.

El valor devuelto DWORD en las versiones de la segunda y terceros, superior, indica si el control de selector de fecha y hora se establece en el estado "sin fecha", como se indica en la [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) miembro de estructura *dwFlags* . Si el valor devuelto es igual a GDT_NONE, el control se establece en estado "sin fecha" y utiliza el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema esté almacenada correctamente en la ubicación de destino.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

Devuelve el tamaño ideal de control de selector de fecha y hora en que se requiere para mostrar la fecha actual o la hora.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*psize*|[out] Puntero a un [tamaño](https://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que contiene el tamaño ideal para el control.|

### <a name="return-value"></a>Valor devuelto

El valor devuelto siempre es TRUE.

### <a name="remarks"></a>Comentarios

Este método envía el [DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_dateTimeCtrl*, que se usa para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente recupera el tamaño ideal para mostrar el control de selector de fecha y hora.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl:: SetFormat

Establece la visualización de un control de selector de fecha y hora con arreglo a una cadena de formato especificado.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parámetros

*pstrFormat*<br/>
Un puntero a una cadena de formato terminada en cero que define la presentación deseada. Si el valor de este parámetro es NULL se restablecerá el control de la cadena de formato predeterminado para el estilo actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

> [!NOTE]
>  Proporcionados por el usuario no determinan el éxito o error para esta llamada.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

Establece el color de una parte determinada del calendario mensual dentro de un control de selector de fecha y hora.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*iColor*<br/>
**int** especificando qué área del control de calendario mensual para establecer el valor. Este valor puede ser uno de los siguientes.

|Valor|Significado|
|-----------|-------------|
|MCSC_BACKGROUND|Establecer el color de fondo que se muestra entre meses.|
|MCSC_MONTHBK|Establecer el color de fondo que se muestra dentro de un mes.|
|MCSC_TEXT|Establezca el color utilizado para mostrar texto en un mes.|
|MCSC_TITLEBK|Establecer el color de fondo que se muestra en el título del calendario.|
|MCSC_TITLETEXT|Establecer el color utilizado para mostrar texto en el título del calendario.|
|MCSC_TRAILINGTEXT|Establezca el color utilizado para mostrar texto de encabezado y al final de día. Encabezado y los días finales son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|

*ref*<br/>
Un valor COLORREF que representa el color que se establecerán para el área especificada del calendario del mes.

### <a name="return-value"></a>Valor devuelto

Un valor COLORREF que representa la configuración de color anterior de la parte especificada del control de calendario mensual si se realiza correctamente. En caso contrario, el mensaje devuelve -1.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl:: SetMonthCalFont

Establece la fuente que utilizará el control de calendario mensual de fecha y hora selector del control secundario.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Identificador de la fuente que se establecerá.

*bRedraw*<br/>
Especifica si el control debe volver a dibujar inmediatamente tras establecer la fuente. Si establece este parámetro en TRUE, el control para actualizarse a sí mismo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Si usa este código, deseará convertir en miembro de su `CDialog`-derivado de la clase denominada *m_MonthFont* de tipo `CFont`.

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

Establece el estilo del control de calendario mensual de lista desplegable que está asociado con el control de selector de fecha y hora actual.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[in] Estilo de control, que es una combinación bit a bit (OR) de los estilos de control de calendario de mes del calendario de un nuevo mes. Para obtener más información, consulte [estilos de Control de calendario de mes](/windows/desktop/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Valor devuelto

El estilo anterior de control de calendario mensual desplegable.

### <a name="remarks"></a>Comentarios

Este método envía el [DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_dateTimeCtrl*, que se usa para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece el control de selector de fecha y hora para mostrar los números de semana, los nombres abreviados de los días de la semana y ningún indicador de hoy.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

Establece las horas de sistema permitido mínimo y máximo para un control de selector de fecha y hora.

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
Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora más temprana permitida en el `CDateTimeCtrl` objeto.

*pMaxRange*<br/>
Un puntero a un `COleDateTime` objeto o un `CTime` objeto que contiene la hora más reciente permitida en el `CDateTimeCtrl` objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange), tal y como se describe en el SDK de Windows. En la implementación de MFC, puede especificar `COleDateTime` o `CTime` usos. Si el `COleDateTime` objeto tiene un estado NULL, se quitará el intervalo. Si el `CTime` puntero o el `COleDateTime` puntero es NULL, se quitará el intervalo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CDateTimeCtrl::GetRange](#getrange).

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

Establece el tiempo en un control de selector de fecha y hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene al que se establecerá el control.

*pTimeNew*<br/>
En la segunda versión anterior, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control. En la tercera versión anterior, un puntero a un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime), tal y como se describe en el SDK de Windows. En la implementación de MFC de `SetTime`, puede usar el `COleDateTime` o `CTime` clases, o bien puede usar un `SYSTEMTIME` estructura, para establecer la información de hora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Vea también

[CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl (clase)](../../mfc/reference/cmonthcalctrl-class.md)
