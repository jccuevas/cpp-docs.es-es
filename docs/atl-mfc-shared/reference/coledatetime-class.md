---
title: Clase COleDateTime
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 610cbec6cb65d4e9616c5e0e0d64e729f39febcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317743"
---
# <a name="coledatetime-class"></a>Clase COleDateTime

Encapsula el `DATE` tipo de datos que se usa en la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDateTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Construye un objeto `COleDateTime`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTime::Format](#format)|Genera una representación de `COleDateTime` cadena con formato de un objeto.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Llame a este método para `COleDateTime` obtener `DBTIMESTAMP` el tiempo en el objeto como una estructura de datos.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Llame a este método para `COleDateTime` obtener el tiempo en el objeto como una estructura de datos [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[COleDateTime::GetAsUDATE](#getasudate)|Llame a este método para `COleDateTime` obtener `UDATE` el tiempo en el como una estructura de datos.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crea `COleDateTime` un objeto que representa la hora actual (función miembro estática).|
|[COleDateTime::GetDay](#getday)|Devuelve el `COleDateTime` día en que representa este objeto (1 - 31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de `COleDateTime` la semana que representa este objeto (domingo 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Devuelve el día del `COleDateTime` año en que representa este objeto (1 de enero a 1).|
|[COleDateTime::GetHour](#gethour)|Devuelve la `COleDateTime` hora en la que representa este objeto (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Devuelve el `COleDateTime` minuto que representa este objeto (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Devuelve el `COleDateTime` mes que representa este objeto (1 - 12).|
|[COleDateTime::GetSecond](#getsecond)|Devuelve el `COleDateTime` segundo que representa este objeto (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Obtiene el estado (validez) `COleDateTime` de este objeto.|
|[COleDateTime::GetYear](#getyear)|Devuelve el `COleDateTime` año que representa este objeto.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Lee un valor de fecha y hora de `COleDateTime`una cadena y establece el valor de .|
|[COleDateTime::SetDate](#setdate)|Establece el valor `COleDateTime` de este objeto en el valor de solo fecha especificado.|
|[COleDateTime::SetDateTime](#setdatetime)|Establece el valor `COleDateTime` de este objeto en el valor de fecha y hora especificado.|
|[COleDateTime::SetStatus](#setstatus)|Establece el status (validez) de este `COleDateTime` objeto.|
|[COleDateTime::SetTime](#settime)|Establece el valor `COleDateTime` de este objeto en el valor de solo tiempo especificado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTime::operator, COleDateTime::operator <, etc.](#coledatetime_relational_operators)|Compare `COleDateTime` dos valores.|
|[COleDateTime::operator +, COleDateTime::operator -](#operator_add_-)|Agregue y `COleDateTime` reste valores.|
|[COleDateTime::operador +-, COleDateTime::operador --](#operator_add_eq_-_eq)|Agregue y `COleDateTime` reste `COleDateTime` un valor de este objeto.|
|[COleDateTime::operator ?](#operator_eq)|Copia `COleDateTime` un valor.|
|[COleDateTime::operator DATE, COleDateTime::operator Date*](#operator_date)|Convierte un `COleDateTime` valor `DATE` en `DATE*`a o un archivo .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Contiene el `DATE` subyacente `COleDateTime` para este objeto.|
|[COleDateTime::m_status](#m_status)|Contiene el estado `COleDateTime` de este objeto.|

## <a name="remarks"></a>Observaciones

`COleDateTime`no tiene una clase base.

Es uno de los tipos posibles para el tipo de datos [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) de automatización OLE. Un `COleDateTime` valor representa un valor absoluto de fecha y hora.

El `DATE` tipo se implementa como un valor de punto flotante. Los días se miden a partir del 30 de diciembre de 1899, a medianoche. En la tabla siguiente se muestran algunas fechas y sus valores asociados:

|Date|Value|
|----------|-----------|
|29 de diciembre de 1899, medianoche|-1.0|
|29 de diciembre de 1899, 6 a.m.|-1.25|
|30 de diciembre de 1899, medianoche|0,0|
|31 de diciembre de 1899, medianoche|1.0|
|1 de enero de 1900, 6 a.m.|2.25|

> [!CAUTION]
> En la tabla anterior, aunque los valores de día se vuelven negativos antes de la medianoche del 30 de diciembre de 1899, los valores de hora del día no lo hacen. Por ejemplo, 6:00 AM siempre está representado por un valor fraccionario 0.25 independientemente de si el entero que representa el día es positivo (después del 30 de diciembre de 1899) o negativo (antes del 30 de diciembre de 1899). Esto significa que una comparación simple de `COleDateTime` puntoflotante ordenaría erróneamente una representación de las 6:00 a.m. del 12/29/1899 como **posterior** a una que representa a las 7:00 a.m. del mismo día.

La `COleDateTime` clase maneja fechas desde el 1 de enero de 100 hasta el 31 de diciembre de 9999. La `COleDateTime` clase utiliza el calendario gregoriano; no soporta las fechas de Julian. `COleDateTime`ignora el horario de verano. (Consulte [Fecha y hora: Soporte de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Puede utilizar `%y` el formato para recuperar un año de dos dígitos solo para fechas a partir de 1900. Si utiliza `%y` el formato en una fecha anterior a 1900, el código genera un error ASSERT.

Este tipo también se utiliza para representar valores de solo fecha o de solo tiempo. Por convención, la fecha 0 (30 de diciembre de 1899) se utiliza para los valores de solo tiempo y la hora 00:00 (medianoche) se utiliza para los valores de solo fecha.

Si crea `COleDateTime` un objeto utilizando una fecha inferior a 100, `GetYear`se `GetMonth` `GetDay`acepta `GetHour`la fecha, pero las llamadas posteriores a , , , `GetMinute`, , y `GetSecond` fail y return -1. Anteriormente, podía usar fechas de dos dígitos, pero las fechas deben ser 100 o más en MFC 4.2 y versiones posteriores.

Para evitar problemas, especifique una fecha de cuatro dígitos. Por ejemplo:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Las operaciones `COleDateTime` aritméticas básicas para los valores utilizan la clase complementaria [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`los valores definen un intervalo de tiempo. La relación entre estas clases es similar a la que hay entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Para obtener más `COleDateTime` `COleDateTimeSpan` información acerca de las clases y, consulte el artículo [Fecha y hora: Compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>COleDateTime Operadores Relacionales

Operadores de comparación.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parámetros

*Fecha*<br/>
Objeto `COleDateTime` que se va a comparar.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Se producirá un ATLASSERT si cualquiera de los dos operandos no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Ejemplo

Los **>=** operadores **>**, **<** ** \< **, , `COleDateTime` y , afirmarán si el objeto se establece en null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDateTime::COleDateTime

Construye un objeto `COleDateTime`.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Parámetros

*dateSrc*<br/>
Objeto `COleDateTime` existente que se va `COleDateTime` a copiar en el nuevo objeto.

*varSrc*<br/>
Estructura `VARIANT` de datos existente `COleVariant` (posiblemente un objeto) que se convertirá en un `COleDateTime` valor de fecha y hora (VT_DATE) y se copie en el nuevo objeto.

*dtSrc*<br/>
Valor de fecha`DATE`y hora ( ) `COleDateTime` que se va a copiar en el nuevo objeto.

*timeSrc*<br/>
A `time_t` `__time64_t` o valor que se convertirá en un valor `COleDateTime` de fecha y hora y copiar en el nuevo objeto.

*systimeSrc*<br/>
Estructura `SYSTEMTIME` que se convertirá en un valor de fecha `COleDateTime` y hora y se copiará en el nuevo objeto.

*filetimeSrc*<br/>
Estructura `FILETIME` que se convertirá en un valor de fecha `COleDateTime` y hora y se copiará en el nuevo objeto. A `FILETIME` utiliza la hora coordinada universal (UTC), por lo que si pasa una hora local en la estructura, los resultados serán incorrectos. Consulte [Tiempos de archivo](/windows/win32/SysInfo/file-times) en el Windows SDK para obtener más información.

*nAño*, *nMes*, *nDía*, *nHour*, *nMin*, *nSec*<br/>
Indique los valores de fecha y hora `COleDateTime` que se van a copiar en el nuevo objeto.

*wDosDate*, *wDosTime*<br/>
Valores de fecha y hora de MS-DOS que se convertirán `COleDateTime` en un valor de fecha y hora y se copiarán en el nuevo objeto.

*Timestamp*<br/>
Una referencia a una estructura [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) que contiene la hora local actual.

### <a name="remarks"></a>Observaciones

Todos estos constructores `COleDateTime` crean nuevos objetos inicializados en el valor especificado. En la tabla siguiente se muestran los intervalos válidos para cada componente de fecha y hora:

|Componente de fecha y hora|Intervalo válido|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

Tenga en cuenta que el límite superior real para el componente de día varía en función de los componentes de mes y año. Para obtener más `SetDate` `SetDateTime` información, consulte las funciones miembro o.

A continuación se muestra una breve descripción de cada constructor:

- `COleDateTime(`**)** Construye `COleDateTime` un objeto inicializado en 0 (medianoche, 30 de diciembre de 1899).

- `COleDateTime(``dateSrc` **)** Construye `COleDateTime` un objeto `COleDateTime` a partir de un objeto existente.

- `COleDateTime(`*varSrc* **)** Construye `COleDateTime` un objeto. Intenta convertir `VARIANT` una estructura o [COleVariant](../../mfc/reference/colevariant-class.md) objeto `VT_DATE`a un valor de fecha y hora ( ). Si esta conversión se realiza correctamente, el `COleDateTime` valor convertido se copia en el nuevo objeto. Si no es así, `COleDateTime` el valor del objeto se establece en 0 (medianoche, 30 de diciembre de 1899) y su estado en no válido.

- `COleDateTime(``dtSrc` **)** Construye `COleDateTime` un objeto `DATE` a partir de un valor.

- `COleDateTime(``timeSrc` **)** Construye `COleDateTime` un objeto `time_t` a partir de un valor.

- `COleDateTime(`*systimeSrc* **)** Construye `COleDateTime` un `SYSTEMTIME` objeto a partir de un valor.

- `COleDateTime(``filetimeSrc` **)** Construye `COleDateTime` un objeto `FILETIME` a partir de un valor. . A `FILETIME` utiliza la hora coordinada universal (UTC), por lo que si pasa una hora local en la estructura, los resultados serán incorrectos. Para obtener más información, consulte [Tiempos de](/windows/win32/SysInfo/file-times) archivo en el Windows SDK.

- `COleDateTime(``nYear`, `nMonth` `nDay`, `nHour` `nMin`, `nSec` , , `COleDateTime` **)** Construye un objeto a partir de los valores numéricos especificados.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Construye `COleDateTime` un objeto a partir de los valores de fecha y hora de MS-DOS especificados.

Para obtener más `time_t` información sobre el tipo de datos, consulte la función [de tiempo](../../c-runtime-library/reference/time-time32-time64.md) en la Referencia de biblioteca en *tiempo de ejecución*.

Para obtener más información, vea las estructuras [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK.

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> El constructor `DBTIMESTAMP` using parámetro sólo está disponible cuando se incluye OLEDB.h.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::Format

Crea una representación con formato del valor de fecha y hora.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica uno de los siguientes indicadores de configuración regional:

- LOCALE_NOUSEROVERRIDE Utilice la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

- VAR_TIMEVALUEONLY Ignore la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY Ignorar la parte de tiempo durante el análisis.

*lcid*<br/>
Indica el ID de configuración regional que se usará para la conversión. Para obtener más información acerca de los identificadores de idioma, vea [Identificadores](/windows/win32/Intl/language-identifiers)de idioma .

*lpszFormat*<br/>
Cadena de formato `printf` similar a la cadena de formato. Cada código de formato, precedido por un signo de porcentaje ( `%`), se reemplaza por el componente correspondiente. `COleDateTime` Otros caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. Para obtener más información, consulte la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). El valor y el significado `Format` de los códigos de formato para son:

- `%H`Horas en el día actual

- `%M`Minutos en la hora actual

- `%S`Segundos en el minuto actual

- `%%`Signo porcentual

*nFormatID*<br/>
El identificador de recurso para la cadena de control de formato.

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene el valor de fecha y hora con formato.

### <a name="remarks"></a>Observaciones

Si el estado `COleDateTime` de este objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena de retorno se especifica mediante el recurso de cadena ATL_IDS_DATETIME_INVALID.

A continuación se presenta una breve descripción de los tres formularios para esta función:

`Format`( *dwFlags*, *lcid*)<br/>
Este formulario da formato al valor mediante las especificaciones de idioma (ideos de configuración regional) para la fecha y la hora. Usando los parámetros predeterminados, este formulario imprimirá la fecha y la hora, a menos que la parte de la hora sea 0 (medianoche), en cuyo caso imprimirá solo la fecha, o la parte de la fecha es 0 (30 de diciembre de 1899), en cuyo caso se imprimirá justo la hora. Si el valor de fecha y hora es 0 (30 de diciembre de 1899, medianoche), este formulario con los parámetros predeterminados imprimirá la medianoche.

`Format`( *lpszFormat*)<br/>
Este formulario da formato al valor mediante la cadena de formato que contiene códigos de formato especiales precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato se pasa como parámetro a la función. Para obtener más información acerca de los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en la referencia de la biblioteca en tiempo de ejecución.

`Format`( *nFormatID*)<br/>
Este formulario da formato al valor mediante la cadena de formato que contiene códigos de formato especiales precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato es un recurso. El identificador de este recurso de cadena se pasa como parámetro. Para obtener más información acerca de los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en la Referencia de la biblioteca en *tiempo de ejecución*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Llame a este método para `COleDateTime` obtener `DBTIMESTAMP` el tiempo en el objeto como una estructura de datos.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parámetros

*Timestamp*<br/>
Una referencia a una estructura [DBTimeStamp.](/dotnet/api/system.data.oledb.oledbtype)

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Almacena el tiempo resultante en la estructura *timeStamp* a la que se hace referencia. La `DBTIMESTAMP` estructura de datos inicializada `fraction` por esta función tendrá su miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDateTime::GetAsSystemTime

Llame a este método para `COleDateTime` obtener `SYSTEMTIME` el tiempo en el objeto como una estructura de datos.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parámetros

*sysTime*<br/>
Una referencia a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir `COleDateTime` el valor de fecha y hora convertido del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE si se produce un `COleDateTime` error en la conversión, o si el objeto es NULL o no es válido.

### <a name="remarks"></a>Observaciones

`GetAsSystemTime`almacena el tiempo resultante en el objeto *sysTime* al que se hace referencia. La `SYSTEMTIME` estructura de datos inicializada `wMilliseconds` por esta función tendrá su miembro establecido en cero.

Para obtener más información sobre `COleDateTime` la información de estado contenida en un objeto, vea [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDateTime::GetAsUDATE

Llame a este método para `COleDateTime` obtener `UDATE` el tiempo en el objeto como una estructura de datos.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parámetros

*uDate*<br/>
Una referencia `UDATE` a una estructura para recibir el `COleDateTime` valor de fecha y hora convertido del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE si se produce un `COleDateTime` error en la conversión, o si el objeto es NULL o no es válido.

### <a name="remarks"></a>Observaciones

Una `UDATE` estructura representa una fecha "desempaquetada".

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Llame a esta función miembro estática para devolver el valor de fecha y hora actual.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime::GetDay

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día del mes representado por `COleDateTime` el `COleDateTime::error` valor de este objeto o si no se pudo obtener el día.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 1 y 31.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDateTime::GetDayOfWeek

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día de la semana representado `COleDateTime` por `COleDateTime::error` el valor de este objeto o si no se pudo obtener el día de la semana.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 1 y 7, donde 1 o domingo, 2 lunes, etc.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Obtiene el día del año representado por este valor de fecha y hora.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día del año representado por `COleDateTime` el `COleDateTime::error` valor de este objeto o si no se pudo obtener el día del año.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 1 y 366, donde el 1 de enero es 1.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDateTime::GetHour

Obtiene la hora representada por este valor de fecha y hora.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

La hora representada por el `COleDateTime` valor `COleDateTime::error` de este objeto o si no se pudo obtener la hora.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 0 y 23.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDateTime::GetMinute

Obtiene el minuto representado por este valor de fecha y hora.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

El minuto representado por el `COleDateTime` valor `COleDateTime::error` de este objeto o si no se pudo obtener el minuto.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 0 y 59.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime::GetMonth

Obtiene el mes representado por este valor de fecha y hora.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

El mes representado por `COleDateTime` el `COleDateTime::error` valor de este objeto o si no se pudo obtener el mes.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 1 y 12.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime::GetSecond

Obtiene el segundo representado por este valor de fecha y hora.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

El segundo representado por el `COleDateTime` valor `COleDateTime::error` de este objeto o si no se pudo obtener el segundo.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 0 y 59.

> [!NOTE]
> La `COleDateTime` clase no admite segundos bisiestos.

Para obtener más información `COleDateTime`acerca de la implementación para , vea el artículo [Fecha y hora: Compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime::GetStatus

Obtiene el estado (validez) `COleDateTime` de un objeto determinado.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado `COleDateTime` de este valor. Si llama `GetStatus` a `COleDateTime` un objeto construido con el valor predeterminado, devolverá validez. Si llama `GetStatus` a `COleDateTime` un objeto inicializado con `GetStatus` el constructor establecido en null, devolverá null.

### <a name="remarks"></a>Observaciones

El valor devuelto se `DateTimeStatus` define mediante el tipo `COleDateTime` enumerado, que se define dentro de la clase.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleDateTime::error`Indica que se ha producido un error al intentar obtener parte del valor de fecha y hora.

- `COleDateTime::valid`Indica que `COleDateTime` este objeto es válido.

- `COleDateTime::invalid`Indica que `COleDateTime` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTime::null`Indica que `COleDateTime` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

El estado `COleDateTime` de un objeto no es válido en los siguientes casos:

- Si su valor se `VARIANT` `COleVariant` establece a partir de un valor o un valor que no se ha podido convertir en un valor de fecha y hora.

- Si su valor se `time_t` `SYSTEMTIME`establece `FILETIME` desde un valor , o que no se pudo convertir en un valor de fecha y hora válido.

- Si su valor `SetDateTime` se establece con valores de parámetro no válidos.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante `+=` `-=`una operación de asignación aritmética, es decir, o .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se `SetStatus`estableció explícitamente en no válido mediante .

Para obtener más información acerca de las operaciones que pueden establecer el estado en no válido, consulte las siguientes funciones miembro:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operador +, -](#operator_add_-)

- [operador +, -](#operator_add_eq_-_eq)

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDateTime::GetYear

Obtiene el año representado por este valor de fecha y hora.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

El año representado por el `COleDateTime` valor `COleDateTime::error` de este objeto o si no se pudo obtener el año.

### <a name="remarks"></a>Observaciones

Los valores devueltos válidos oscilan entre 100 y 9999, que incluye el siglo.

Para obtener información sobre otras funciones `COleDateTime` miembro que consultan el valor de este objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDateTime::m_dt

La estructura `DATE` subyacente `COleDateTime` para este objeto.

```
DATE m_dt;
```

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> Cambiar el valor `DATE` en el objeto al que tiene acceso `COleDateTime` el puntero devuelto por esta función cambiará el valor de este objeto. No cambia el estado `COleDateTime` de este objeto.

Para obtener más información `DATE` acerca de la implementación del objeto, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDateTime::m_status

Contiene el estado `COleDateTime` de este objeto.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Observaciones

El tipo de este miembro de `DateTimeStatus`datos es el `COleDateTime` tipo enumerado, que se define dentro de la clase. Para obtener más información, vea [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
> Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para obtener más precauciones con respecto a la configuración explícita de este miembro de datos.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::operator ?

Copia `COleDateTime` un valor.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Observaciones

Estos operadores de asignación sobrecargados copian el valor de fecha y hora de origen en este `COleDateTime` objeto. A continuación se ofrece una breve descripción de cada uno de estos operadores de asignación sobrecargados:

- **Operador (** `dateSrc` **)** El valor y el estado del `COleDateTime` operando se copian en este objeto.

- **operador (** *varSrc* **)** Si la conversión del valor [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) (o [cOleVariant](../../mfc/reference/colevariant-class.md) objeto) a una fecha y hora `COleDateTime` (VT_DATE) es correcta, el valor convertido se copia en este objeto y su estado se establece en válido. Si la conversión no se realiza correctamente, el valor de este objeto se establece en cero (30 de diciembre de 1899, medianoche) y su estado no es válido.

- **Operador (** `dtSrc` **)** El `DATE` valor se copia `COleDateTime` en este objeto y su estado se establece en válido.

- **Operador (** `timeSrc` **)** El `time_t` `__time64_t` valor o se convierte `COleDateTime` y se copia en este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; si no se realiza correctamente, se establece en no válido.

- **operador (** *systimeSrc* **)** El valor [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) se convierte `COleDateTime` y se copia en este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; si no se realiza correctamente, se establece en no válido.

- **Operador (** `uDate` **)** El `UDATE` valor se convierte y `COleDateTime` se copia en este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; si no se realiza correctamente, se establece en no válido. Una `UDATE` estructura representa una fecha "desempaquetada". Para obtener más información, consulte la función [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **Operador (** `filetimeSrc` **)** El valor [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) se convierte `COleDateTime` y se copia en este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; de lo contrario, se establece en no válido. `FILETIME`utiliza la hora coordinada universal (UTC), por lo que si pasa una hora UTC en la estructura, los resultados se convertirán de la hora UTC a la hora local y se almacenarán como hora variante. Este comportamiento es el mismo que en Visual C++ 6.0 y Visual C++.NET 2003 SP2. Para obtener más información, consulte [Tiempos de](/windows/win32/SysInfo/file-times) archivo en el Windows SDK.

Para obtener más información, consulte la entrada [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

Para obtener más `time_t` información sobre el tipo de datos, consulte la función [de tiempo](../../c-runtime-library/reference/time-time32-time64.md) en la Referencia de biblioteca en *tiempo de ejecución*.

Para obtener más información, vea las estructuras [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK.

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::operador +, -

Agregue y `ColeDateTime` reste valores.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Observaciones

`COleDateTime`objetos representan tiempos absolutos. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) objetos representan tiempos relativos. Los dos primeros operadores le `COleDateTimeSpan` permiten agregar `COleDateTime` y restar un valor de un valor. El tercer operador le `COleDateTime` permite restar un `COleDateTimeSpan` valor de otro para producir un valor.

Si cualquiera de los operandos es null, el estado del valor resultante `COleDateTime` es null.

Si el `COleDateTime` valor resultante queda fuera de los límites `COleDateTime` de valores aceptables, el estado de ese valor no es válido.

Si cualquiera de los operandos no es válido y el `COleDateTime` otro no es null, el estado del valor resultante no es válido.

Los **+** **-** operadores y `COleDateTime` afirmarán si el objeto se establece en null. Vea [COleDateTime Operadores relacionales](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTime::operador +-, --

Agregue y `ColeDateTime` reste `COleDateTime` un valor de este objeto.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Observaciones

Estos operadores le permiten `COleDateTimeSpan` agregar y restar un valor a y desde este `COleDateTime`archivo . Si cualquiera de los operandos es null, el estado del valor resultante `COleDateTime` es null.

Si el `COleDateTime` valor resultante queda fuera de los límites `COleDateTime` de los valores aceptables, el estado de este valor se establece en no válido.

Si cualquiera de los operandos no es válido y `COleDateTime` otro no es null, el estado del valor resultante no es válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

Los **+=** **-=** operadores y `COleDateTime` afirmarán si el objeto se establece en null. Vea [COleDateTime Operadores relacionales](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDateTime::operator DATE

Convierte un `ColeDateTime` valor `DATE`en un archivo .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Observaciones

Este operador `DATE` devuelve un objeto cuyo `COleDateTime` valor se copia de este objeto. Para obtener más información `DATE` acerca de la implementación del objeto, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

El `DATE` operador afirmará `COleDateTime` si el objeto se establece en null. Vea [COleDateTime Operadores relacionales](#coledatetime_relational_operators) para obtener un ejemplo.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::ParseDateTime

Analiza una cadena para leer un valor de fecha y hora.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*lpszDate*<br/>
Puntero a la cadena terminada en null que se va a analizar. Para conocer más detalles, vea la sección Comentarios.

*dwFlags*<br/>
Indica los indicadores para la configuración regional y el análisis. Uno o más de los siguientes indicadores:

- LOCALE_NOUSEROVERRIDE Utilice la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

- VAR_TIMEVALUEONLY Ignore la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY Ignorar la parte de tiempo durante el análisis.

*lcid*<br/>
Indica el ID de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se convirtió correctamente en un valor de fecha y hora, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

Si la cadena se convirtió correctamente en un valor `COleDateTime` de fecha y hora, el valor de este objeto se establece en ese valor y su estado en válido.

> [!NOTE]
> Los valores de año deben estar entre 100 y 9999, ambos inclusive.

El parámetro *lpszDate* puede tomar una variedad de formatos. Por ejemplo, las siguientes cadenas contienen formatos de fecha y hora aceptables:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

El identificador de configuración regional también afectará a si el formato de cadena es aceptable para la conversión a un valor de fecha y hora.

En el caso de VAR_DATEVALUEONLY, el valor de hora se establece en la hora 0 o medianoche. En el caso de VAR_TIMEVALUEONLY, el valor de fecha se establece en la fecha 0, es decir, el 30 de diciembre de 1899.

Si la cadena no se pudo convertir en un valor de fecha y `COleDateTime` hora o si hubo un desbordamiento numérico, el estado de este objeto no es válido.

Para obtener más información acerca `COleDateTime` de los límites y la implementación de valores, consulte el artículo [Fecha y hora: Compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDateTime::SetDate

Establece la fecha `COleDateTime` de este objeto.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parámetros

*nAño*, *nMes*, *nDía*<br/>
Indique los componentes de fecha `COleDateTime` que se van a copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el `COleDateTime` valor de este objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se `DateTimeStatus` basa en el tipo enumerado. Para obtener más información, vea el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Observaciones

La fecha se establece en los valores especificados. La hora se establece en la hora 0, medianoche.

Consulte la tabla siguiente para ver los límites de los valores de parámetro:

|Parámetro|Bounds|
|---------------|------------|
|*nAño*|100 - 9999|
|*nMes*|1 - 12|
|*nDay*|0 - 31|

Si el día del mes se desborda, se convierte al día correcto del mes siguiente y el mes o año se incrementa en consecuencia. Un valor de día de cero indica el último día del mes anterior. El comportamiento es `SystemTimeToVariantTime`el mismo que .

Si el valor de fecha especificado por los parámetros no `COleDateTime::invalid`es válido, el estado de este objeto se establece en . Debe usar [GetStatus](#getstatus) para comprobar la `DATE` validez del valor y no debe suponer que el valor de [m_dt](#m_dt) permanecerá sin modificar.

Estos son algunos ejemplos de valores de fecha:

|*nAño*|*nMes*|*nDay*|Value|
|-------------|--------------|------------|-----------|
|2000|2|29|29 de febrero de 2000|
|1776|7|4|4 de julio de 1776|
|1925|4|35|35 de abril de 1925 (fecha no válida)|
|10000|1|1|1 de enero de 10000 (fecha no válida)|

Para establecer la fecha y la hora, vea [COleDateTime::SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultan el valor de este `COleDateTime` objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDateTime::SetDateTime

Establece la fecha y `COleDateTime` la hora de este objeto.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parámetros

*nAño*, *nMes*, *nDía*, *nHour*, *nMin*, *nSec*<br/>
Indique los componentes de fecha y `COleDateTime` hora que se van a copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el `COleDateTime` valor de este objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se `DateTimeStatus` basa en el tipo enumerado. Para obtener más información, vea el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Observaciones

Consulte la tabla siguiente para ver los límites de los valores de parámetro:

|Parámetro|Bounds|
|---------------|------------|
|*nAño*|100 - 9999|
|*nMes*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si el día del mes se desborda, se convierte al día correcto del mes siguiente y el mes o año se incrementa en consecuencia. Un valor de día de cero indica el último día del mes anterior. El comportamiento es el mismo que [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si el valor de fecha u hora especificado por los parámetros no es válido, el estado de este objeto se establece en no válido y el valor de este objeto no cambia.

Estos son algunos ejemplos de valores de tiempo:

|*nHour*|*nMin*|*nSec*|Value|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válida|
|9|60|0|No válida|

Estos son algunos ejemplos de valores de fecha:

|*nAño*|*nMes*|*nDay*|Value|
|-------------|--------------|------------|-----------|
|1995|4|15|15 de abril de 1995|
|1789|7|14|17 de julio de 1789|
|1925|2|30|No válida|
|10000|1|1|No válida|

Para establecer solo la fecha, vea [COleDateTime::SetDate](#setdate). Para establecer solo la hora, vea [COleDateTime::SetTime](#settime).

Para obtener información sobre las funciones miembro que consultan el valor de este `COleDateTime` objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDateTime::SetStatus

Establece el estado `COleDateTime` de este objeto.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El nuevo valor `COleDateTime` de estado para este objeto.

### <a name="remarks"></a>Observaciones

El *status* valor del parámetro `DateTimeStatus` status se define mediante el `COleDateTime` tipo enumerado, que se define dentro de la clase. Consulte [COleDateTime::GetStatus](#getstatus) para obtener más información.

> [!CAUTION]
> Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se usará más a menudo para establecer el estado en **null** o **invalid .** El operador de asignación ([operator )](#operator_eq)y [SetDateTime](#setdatetime) establecen el estado del objeto en función de los valores de origen.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::SetTime

Establece la hora `COleDateTime` de este objeto.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parámetros

*nHora*, *nMin*, *nSec*<br/>
Indique los componentes de tiempo `COleDateTime` que se van a copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el `COleDateTime` valor de este objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se `DateTimeStatus` basa en el tipo enumerado. Para obtener más información, vea el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Observaciones

La hora se establece en los valores especificados. La fecha se establece en la fecha 0, lo que significa el 30 de diciembre de 1899.

Consulte la tabla siguiente para ver los límites de los valores de parámetro:

|Parámetro|Bounds|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si el valor de tiempo especificado por los parámetros no es válido, el estado de este objeto se establece en no válido y el valor de este objeto no cambia.

Estos son algunos ejemplos de valores de tiempo:

|*nHour*|*nMin*|*nSec*|Value|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válida|
|9|60|0|No válida|

Para establecer la fecha y la hora, vea [COleDateTime::SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultan el valor de este `COleDateTime` objeto, consulte las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información `COleDateTime` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [SetDate](#setdate).

## <a name="see-also"></a>Consulte también

[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[Clase CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Clase CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
