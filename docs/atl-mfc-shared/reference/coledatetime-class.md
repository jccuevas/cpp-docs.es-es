---
title: COleDateTime (clase)
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
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491256"
---
# <a name="coledatetime-class"></a>COleDateTime (clase)

Encapsula el `DATE` tipo de datos que se utiliza en la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDateTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Construye un objeto `COleDateTime`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDateTime::Format](#format)|Genera una representación de cadena con formato `COleDateTime` de un objeto.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Llame a este método para obtener la hora `COleDateTime` del objeto como una `DBTIMESTAMP` estructura de datos.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Llame a este método para obtener la hora `COleDateTime` del objeto como una estructura de datos [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[COleDateTime::GetAsUDATE](#getasudate)|Llame a este método para obtener la hora de `COleDateTime` como una `UDATE` estructura de datos.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crea un `COleDateTime` objeto que representa la hora actual (función miembro estática).|
|[COleDateTime::GetDay](#getday)|Devuelve el día que `COleDateTime` representa este objeto (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de la semana que `COleDateTime` representa este objeto (Sunday = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Devuelve el día del año que representa `COleDateTime` este objeto (ene 1 = 1).|
|[COleDateTime::GetHour](#gethour)|Devuelve la hora que `COleDateTime` representa este objeto (0-23).|
|[COleDateTime::GetMinute](#getminute)|Devuelve el minuto que `COleDateTime` representa este objeto (0-59).|
|[COleDateTime::GetMonth](#getmonth)|Devuelve el mes que `COleDateTime` representa este objeto (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Devuelve el segundo que `COleDateTime` este objeto representa (0-59).|
|[COleDateTime::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleDateTime` objeto.|
|[COleDateTime::GetYear](#getyear)|Devuelve el año que `COleDateTime` representa este objeto.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Lee un valor de fecha y hora de una cadena y establece el valor `COleDateTime`de.|
|[COleDateTime::SetDate](#setdate)|Establece el valor de este `COleDateTime` objeto en el valor de solo fecha especificado.|
|[COleDateTime::SetDateTime](#setdatetime)|Establece el valor de este `COleDateTime` objeto en el valor de fecha y hora especificado.|
|[COleDateTime::SetStatus](#setstatus)|Establece el estado (validez) de este `COleDateTime` objeto.|
|[COleDateTime::SetTime](#settime)|Establece el valor de este `COleDateTime` objeto en el valor de solo hora especificado.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDateTime:: Operator = =, COleDateTime:: Operator <, etc.](#coledatetime_relational_operators)|Compara dos `COleDateTime` valores.|
|[COleDateTime:: Operator +, COleDateTime:: Operator-](#operator_add_-)|Agregue y reste `COleDateTime` valores.|
|[COleDateTime:: Operator + =, COleDateTime:: Operator-=](#operator_add_eq_-_eq)|Agregue y reste un `COleDateTime` valor de este `COleDateTime` objeto.|
|[COleDateTime:: Operator =](#operator_eq)|Copia un `COleDateTime` valor.|
|[COleDateTime:: Operator DATE, COleDateTime:: Operator Date *](#operator_date)|Convierte un `COleDateTime` valor `DATE` en o `DATE*`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Contiene el subyacente `DATE` de este `COleDateTime` objeto.|
|[COleDateTime::m_status](#m_status)|Contiene el estado de este `COleDateTime` objeto.|

## <a name="remarks"></a>Comentarios

`COleDateTime`no tiene una clase base.

Es uno de los tipos posibles para el tipo de datos [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) de la automatización OLE. Un `COleDateTime` valor representa un valor de fecha y hora absoluto.

El `DATE` tipo se implementa como un valor de punto flotante. Los días se miden desde el 30 de diciembre de 1899, a medianoche. En la tabla siguiente se muestran algunas fechas y sus valores asociados:

|Date|Valor|
|----------|-----------|
|29 de diciembre de 1899, medianoche|-1.0|
|29 de diciembre de 1899, 6 A. M|-1.25|
|30 de diciembre de 1899, medianoche|0.0|
|31 de diciembre de 1899, medianoche|1.0|
|1 de enero de 1900, 6 A.M.|2.25|

> [!CAUTION]
> En la tabla anterior, aunque los valores de día se vuelven negativos antes de la medianoche del 30 de diciembre de 1899, los valores de hora del día no lo hacen. Por ejemplo, 6:00 AM siempre se representa mediante un valor fraccionario 0,25, con independencia de si el entero que representa el día es positivo (después del 30 de diciembre de 1899) o negativo (antes del 30 de diciembre de 1899). Esto significa que una comparación simple de puntos flotantes ordenaría erróneamente un `COleDateTime` que represente 6:00 AM en 12/29/1899 como **más tarde** que un que representa 7:00 AM en el mismo día.

La `COleDateTime` clase controla las fechas desde el 1 de enero de 100 hasta el 31 de diciembre de 9999. La `COleDateTime` clase utiliza el calendario gregoriano; no admite fechas Juliano. `COleDateTime`omite el horario de verano. (Vea [fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)automatización).

> [!NOTE]
> Puede usar el `%y` formato para recuperar un año de dos dígitos solo para fechas a partir de 1900. Si usa el `%y` formato en una fecha anterior a 1900, el código genera un error de aserción.

Este tipo también se usa para representar valores de solo fecha o solo de hora. Por Convención, la fecha 0 (30 de diciembre de 1899) se usa para los valores de solo hora y la hora 00:00 (medianoche) se usa para los valores de solo fecha.

`COleDateTime` Si crea un objeto con una fecha inferior a 100, se acepta la fecha, pero las llamadas subsiguientes `GetYear`a `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, y `GetSecond` producen un error y devuelven-1. Anteriormente, podía usar fechas de dos dígitos, pero las fechas deben ser 100 o mayores en MFC 4,2 y versiones posteriores.

Para evitar problemas, especifique una fecha de cuatro dígitos. Por ejemplo:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Las operaciones aritméticas básicas `COleDateTime` para los valores usan la clase complementaria [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`los valores definen un intervalo de tiempo. La relación entre estas clases es similar a la de [ctime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Para obtener más información sobre `COleDateTime` las `COleDateTimeSpan` clases y, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

## <a name="requirements"></a>Requisitos

**Encabezado**: ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>Operadores relacionales de COleDateTime

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

*date*<br/>
Objeto `COleDateTime` que se va a comparar.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Se producirá una ATLASSERT si alguno de los dos operandos no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Ejemplo

Los operadores **>=** **\< ,=** , y ,validarán`COleDateTime` si el objeto está establecido en NULL. **<** **>**

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>COleDateTime:: COleDateTime

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
Objeto existente `COleDateTime` que se va a copiar en el `COleDateTime` nuevo objeto.

*varSrc*<br/>
Una estructura `VARIANT` de datos existente (posiblemente `COleVariant` un objeto) que se va a convertir en un valor de fecha y hora (VT_DATE) y `COleDateTime` copiar en el nuevo objeto.

*dtSrc*<br/>
Valor de fecha y hora`DATE`() que se va a copiar en `COleDateTime` el nuevo objeto.

*timeSrc*<br/>
Un `time_t` valor `__time64_t` o que se va a convertir en un valor de fecha y hora y copiarse en el nuevo `COleDateTime` objeto.

*systimeSrc*<br/>
Estructura que se va a convertir en un valor de fecha y hora y que se `COleDateTime` va a copiar en el nuevo objeto. `SYSTEMTIME`

*filetimeSrc*<br/>
Estructura que se va a convertir en un valor de fecha y hora y que se `COleDateTime` va a copiar en el nuevo objeto. `FILETIME` Un `FILETIME` usa el horario universal coordinado (UTC), por lo que si se pasa una hora local en la estructura, los resultados serán incorrectos. Consulte los [tiempos de archivo](/windows/win32/SysInfo/file-times) en el Windows SDK para obtener más información.

*nYear*, *nMonth*, *ndía*, *Nhora*, *nmín.* , *nSec*<br/>
Indica los valores de fecha y hora que se van a copiar `COleDateTime` en el nuevo objeto.

*wDosDate*, *wDosTime*<br/>
Valores de fecha y hora de ms-dos que se convertirán en un valor de fecha y hora y `COleDateTime` se copiarán en el nuevo objeto.

*timeStamp*<br/>
Referencia a una estructura [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) que contiene la hora local actual.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleDateTime` objetos inicializados en el valor especificado. En la tabla siguiente se muestran los intervalos válidos para cada componente de fecha y hora:

|Componente de fecha y hora|Intervalo válido|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|queda|0 - 59|
|second|0 - 59|

Tenga en cuenta que el límite superior real para el componente de día varía en función de los componentes de mes y año. Para obtener más información, `SetDate` vea `SetDateTime` las funciones miembro o.

A continuación se describe brevemente cada constructor:

- `COleDateTime(` **)** Crea un `COleDateTime` objeto inicializado en 0 (medianoche, 30 de diciembre de 1899).

- `COleDateTime(`) Construye un `COleDateTime` objeto a partir de un `COleDateTime` objeto existente. `dateSrc`

- `COleDateTime(`*varSrc* **)** Construye un `COleDateTime` objeto. Intenta convertir una estructura `VARIANT` o un objeto [COleVariant](../../mfc/reference/colevariant-class.md) en un valor de fecha y `VT_DATE`hora (). Si esta conversión se realiza correctamente, el valor convertido se copia en el `COleDateTime` nuevo objeto. Si no es así, el valor del `COleDateTime` objeto se establece en 0 (medianoche, 30 de diciembre de 1899) y su estado en no válido.

- `COleDateTime(`) Construye un `COleDateTime` objeto a partir de `DATE` un valor. `dtSrc`

- `COleDateTime(`) Construye un `COleDateTime` objeto a partir de `time_t` un valor. `timeSrc`

- `COleDateTime(`*systimeSrc* **)** Construye un `COleDateTime` objeto a partir de `SYSTEMTIME` un valor.

- `COleDateTime(`) Construye un `COleDateTime` objeto a partir de `FILETIME` un valor. `filetimeSrc` . Un `FILETIME` usa el horario universal coordinado (UTC), por lo que si se pasa una hora local en la estructura, los resultados serán incorrectos. Para obtener más información, vea [horas de archivo](/windows/win32/SysInfo/file-times) en el Windows SDK.

- `COleDateTime(``nYear`, ,,`nDay`,,) Construye un objeto`COleDateTime` a partir de los valores numéricos especificados. `nHour` `nMin` `nMonth` `nSec`

- `COleDateTime(``wDosDate`, )`wDosTime` Construye un`COleDateTime` objeto a partir de los valores de fecha y hora de ms-dos especificados.

Para obtener más información sobre `time_t` el tipo de datos, vea la función [Time](../../c-runtime-library/reference/time-time32-time64.md) en la referencia de la *biblioteca en tiempo de ejecución*.

Para obtener más información, vea las estructuras [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK.

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

> [!NOTE]
> El constructor que `DBTIMESTAMP` usa el parámetro solo está disponible cuando se incluye OleDb. h.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

Crea una representación con formato del valor de fecha y hora.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica una de las siguientes marcas de configuración regional:

- LOCALE_NOUSEROVERRIDE usa la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

- VAR_TIMEVALUEONLY omite la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY omite la parte de hora durante el análisis.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión. Para obtener más información sobre los identificadores de idioma, vea identificadores de [idioma](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Cadena de formato similar a la `printf` cadena de formato. Cada código de formato, precedido por un signo `%`de porcentaje (), se reemplaza por `COleDateTime` el componente correspondiente. Los demás caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. Para obtener más información, vea la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). El valor y el significado de los códigos de `Format` formato de son:

- `%H`Horas en el día actual

- `%M`Minutos de la hora actual

- `%S`Segundos en el minuto actual

- `%%`Signo de porcentaje

*nFormatID*<br/>
IDENTIFICADOR de recurso de la cadena de control de formato.

### <a name="return-value"></a>Valor devuelto

`CString` Que contiene el valor de fecha y hora con formato.

### <a name="remarks"></a>Comentarios

Si el estado de este `COleDateTime` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta se especifica mediante el recurso de cadena ATL_IDS_DATETIME_INVALID.

A continuación se ofrece una breve descripción de las tres formas de esta función:

`Format`( *dwFlags*, *lcid*)<br/>
Este formulario da formato al valor usando las especificaciones de idioma (identificadores de configuración regional) de fecha y hora. Con los parámetros predeterminados, este formulario imprimirá la fecha y la hora, a menos que la parte de la hora sea 0 (medianoche), en cuyo caso se imprimirá solo la fecha o la parte de la fecha será 0 (30 de diciembre de 1899), en cuyo caso se imprimirá solo la hora. Si el valor de fecha y hora es 0 (30 de diciembre de 1899, medianoche), este formulario con los parámetros predeterminados se imprimirá a medianoche.

`Format`( *lpszFormat*)<br/>
Este formulario da formato al valor usando la cadena de formato que contiene códigos de formato especiales precedidos por un signo de porcentaje (%), `printf`como en. La cadena de formato se pasa como un parámetro a la función. Para obtener más información sobre los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en la referencia de la biblioteca en tiempo de ejecución.

`Format`( *nFormatID*)<br/>
Este formulario da formato al valor usando la cadena de formato que contiene códigos de formato especiales precedidos por un signo de porcentaje (%), `printf`como en. La cadena de formato es un recurso. El identificador de este recurso de cadena se pasa como parámetro. Para obtener más información sobre los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en la referencia de la *biblioteca en tiempo de ejecución*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>COleDateTime:: GetAsDBTIMESTAMP

Llame a este método para obtener la hora `COleDateTime` del objeto como una `DBTIMESTAMP` estructura de datos.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parámetros

*timeStamp*<br/>
Referencia a una estructura [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Almacena la hora resultante en la estructura de *marca* de tiempo a la que se hace referencia. La `DBTIMESTAMP` estructura de datos inicializada por esta función tendrá su `fraction` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

Llame a este método para obtener la hora `COleDateTime` del objeto como una `SYSTEMTIME` estructura de datos.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parámetros

*sysTime*<br/>
Referencia a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir el valor de fecha y hora convertido del `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto; FALSE si se produce un error en la conversión `COleDateTime` , o si el objeto es null o no es válido.

### <a name="remarks"></a>Comentarios

`GetAsSystemTime`almacena la hora resultante en el objeto *sysTime* al que se hace referencia. La `SYSTEMTIME` estructura de datos inicializada por esta función tendrá su `wMilliseconds` miembro establecido en cero.

Para obtener más información sobre la información de estado contenida en un `COleDateTime` objeto, vea [getStatus](#getstatus).

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

Llame a este método para obtener la hora `COleDateTime` del objeto como una `UDATE` estructura de datos.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parámetros

*uDate*<br/>
Referencia a una `UDATE` estructura para recibir el valor `COleDateTime` de fecha y hora convertido del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto; FALSE si se produce un error en la conversión `COleDateTime` , o si el objeto es null o no es válido.

### <a name="remarks"></a>Comentarios

Una `UDATE` estructura representa una fecha "desempaquetada".

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

Llame a esta función miembro estática para devolver el valor de fecha y hora actual.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>COleDateTime:: getDay (

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

Día del mes representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 1 y 31.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día de la semana representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día de la semana.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 1 y 7, donde 1 = Domingo, 2 = lunes, etc.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

Obtiene el día del año representado por este valor de fecha y hora.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

Día del año representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día del año.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 1 y 366, donde 1 de enero = 1.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>COleDateTime:: GetHour

Obtiene la hora representada por este valor de fecha y hora.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

La hora representada por el valor `COleDateTime` de este `COleDateTime::error` objeto o si no se pudo obtener la hora.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 0 y 23.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>COleDateTime:: GetMinute

Obtiene el minuto representado por este valor de fecha y hora.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

El minuto representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el minuto.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 0 y 59.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getmonth"></a>COleDateTime:: GetMonth

Obtiene el mes representado por este valor de fecha y hora.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Mes representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el mes.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 1 y 12.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getDay (](#getday).

##  <a name="getsecond"></a>  COleDateTime::GetSecond

Obtiene el segundo representado por este valor de fecha y hora.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

Segundo representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el segundo.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 0 y 59.

> [!NOTE]
>  La `COleDateTime` clase no admite los segundos bisiestos.

Para obtener más información acerca de la `COleDateTime`implementación de para, [vea el artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getstatus"></a>  COleDateTime::GetStatus

Obtiene el estado (validez) de un objeto `COleDateTime` determinado.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado de este `COleDateTime` valor. Si llama `GetStatus` a en un `COleDateTime` objeto construido con el valor predeterminado, devolverá un valor válido. Si llama `GetStatus` a en un `COleDateTime` objeto inicializado con el constructor establecido en null, `GetStatus` devolverá null.

### <a name="remarks"></a>Comentarios

El valor devuelto se define mediante `DateTimeStatus` el tipo enumerado, que se define dentro `COleDateTime` de la clase.

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

- `COleDateTime::valid`Indica que este `COleDateTime` objeto es válido.

- `COleDateTime::invalid`Indica que este `COleDateTime` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTime::null`Indica que este `COleDateTime` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

El estado de un `COleDateTime` objeto no es válido en los casos siguientes:

- Si su valor se establece a partir `VARIANT` de `COleVariant` un valor o que no se pudo convertir en un valor de fecha y hora.

- Si su valor se establece en un `time_t`valor `SYSTEMTIME`de, `FILETIME` o que no se pudo convertir en un valor de fecha y hora válido.

- Si su valor se establece `SetDateTime` con valores de parámetro no válidos.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmética, es decir `+=` , `-=`o.

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no `SetStatus`válido mediante.

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, vea las siguientes funciones miembro:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operador +,-](#operator_add_-)

- [operator +=, -=](#operator_add_eq_-_eq)

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>COleDateTime:: GetYear

Obtiene el año representado por este valor de fecha y hora.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

El año representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el año.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 100 y 9999, que incluye el siglo.

Para obtener información sobre otras funciones miembro que consultan el valor `COleDateTime` de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getDay (](#getday).

##  <a name="m_dt"></a>  COleDateTime::m_dt

La estructura `DATE` subyacente de este `COleDateTime` objeto.

```
DATE m_dt;
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Si cambia el valor `DATE` del objeto al que tiene acceso el puntero devuelto por esta función, cambiará el valor de este `COleDateTime` objeto. No cambia el estado de este `COleDateTime` objeto.

Para obtener más información sobre la implementación del `DATE` objeto, vea el artículo [fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

##  <a name="m_status"></a>  COleDateTime::m_status

Contiene el estado de este `COleDateTime` objeto.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Comentarios

El tipo de este miembro de datos es el tipo `DateTimeStatus`enumerado, que se define en la `COleDateTime` clase. Para obtener más información, vea [COleDateTime:: getStatus](#getstatus).

> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [getStatus](#getstatus) y [SetStatus](#setstatus). Vea `SetStatus` para obtener más precauciones relacionadas con la configuración explícita de este miembro de datos.

##  <a name="operator_eq"></a>COleDateTime:: Operator =

Copia un `COleDateTime` valor.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Comentarios

Estos operadores de asignación sobrecargados copian el valor de fecha y hora `COleDateTime` de origen en este objeto. A continuación se ofrece una breve descripción de cada uno de estos operadores de asignación sobrecargados:

- **Operator = (** `dateSrc` **)** el valor y el estado del operando se copian `COleDateTime` en este objeto.

- **Operator = (** *varSrc* **)** Si la conversión del valor [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) (u objeto [COleVariant](../../mfc/reference/colevariant-class.md) ) en una fecha y hora (VT_DATE) es correcta, el valor convertido se copia en este `COleDateTime` objeto y su estado se establece en Valid. Si la conversión no se realiza correctamente, el valor de este objeto se establece en cero (30 de diciembre de 1899, medianoche) y su estado en no válido.

- **Operator = (** `dtSrc` **)** el `DATE` valor se copia en este `COleDateTime` objeto y su estado se establece en Valid.

- **Operator = (** `timeSrc` **)** el `time_t` valor `__time64_t` o se convierte y se copia en `COleDateTime` este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en Valid; Si no se realiza correctamente, se establece en no válido.

- **Operator = (** *systimeSrc* **)** El valor [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) se convierte y se copia en `COleDateTime` este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en Valid; Si no se realiza correctamente, se establece en no válido.

- **Operator = (** `uDate` **)** el `UDATE` valor se convierte y se copia en `COleDateTime` este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en Valid; Si no se realiza correctamente, se establece en no válido. Una `UDATE` estructura representa una fecha "desempaquetada". Para obtener más información, vea la función [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **Operator = (** `filetimeSrc` **)** el valor [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) se convierte y se copia en `COleDateTime` este objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en Valid; en caso contrario, se establece en no válido. `FILETIME`usa el horario universal coordinado (UTC), por lo que si se pasa una hora UTC en la estructura, los resultados se convertirán de la hora UTC a la hora local y se almacenarán como hora de variante. Este comportamiento es el mismo que en Visual C++ 6,0 y visual C++.NET 2003 SP2. Para obtener más información, vea [horas de archivo](/windows/win32/SysInfo/file-times) en el Windows SDK.

Para obtener más información, vea la entrada [variante](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

Para obtener más información sobre `time_t` el tipo de datos, vea la función [Time](../../c-runtime-library/reference/time-time32-time64.md) en la referencia de la *biblioteca en tiempo de ejecución*.

Para obtener más información, vea las estructuras [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK.

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

##  <a name="operator_add_-"></a>COleDateTime:: Operator +,-

Agregue y reste `ColeDateTime` valores.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Comentarios

`COleDateTime`los objetos representan las horas absolutas. Los objetos [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) representan los tiempos relativos. Los dos primeros operadores permiten agregar y sustraer un `COleDateTimeSpan` valor de un `COleDateTime` valor. El tercer operador permite restar un `COleDateTime` valor de otro para producir un `COleDateTimeSpan` valor.

Si alguno de los operandos es null, el estado del valor resultante `COleDateTime` es NULL.

Si el valor `COleDateTime` resultante está fuera de los límites de los valores aceptables, el estado `COleDateTime` de ese valor no es válido.

Si alguno de los operandos no es válido y el otro no es null, el estado del valor resultante `COleDateTime` no es válido.

Los **+** operadores **-** y validarán si el `COleDateTime` objeto está establecido en NULL. Vea los [operadores relacionales de COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>COleDateTime:: Operator + =,-=

Agregue y reste un `ColeDateTime` valor de este `COleDateTime` objeto.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Comentarios

Estos operadores permiten agregar y sustraer un `COleDateTimeSpan` valor a y desde este. `COleDateTime` Si alguno de los operandos es null, el estado del valor resultante `COleDateTime` es NULL.

Si el valor `COleDateTime` resultante está fuera de los límites de los valores aceptables, el estado `COleDateTime` de este valor se establece en no válido.

Si alguno de los operandos no es válido y otro no es null, el estado del valor resultante `COleDateTime` no es válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

Los **+=** operadores **-=** y validarán si el `COleDateTime` objeto está establecido en NULL. Vea los [operadores relacionales de COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

##  <a name="operator_date"></a>COleDateTime:: Operator fecha

Convierte un `ColeDateTime` valor `DATE`en.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve un `DATE` objeto cuyo valor se copia desde este `COleDateTime` objeto. Para obtener más información sobre la implementación del `DATE` objeto, vea el artículo [fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

El `DATE` operador validará si el `COleDateTime` objeto está establecido en NULL. Vea los [operadores relacionales de COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

##  <a name="parsedatetime"></a>COleDateTime::P arseDateTime

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
Indica las marcas para la configuración regional y el análisis. Una o varias de las marcas siguientes:

- LOCALE_NOUSEROVERRIDE usa la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

- VAR_TIMEVALUEONLY omite la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY omite la parte de hora durante el análisis.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se convirtió correctamente en un valor de fecha y hora; de lo contrario, es FALSE.

### <a name="remarks"></a>Comentarios

Si la cadena se convirtió correctamente en un valor de fecha y hora, el valor `COleDateTime` de este objeto se establece en ese valor y su estado en válido.

> [!NOTE]
>  Los valores de año deben estar entre 100 y 9999, ambos inclusive.

El parámetro *lpszDate* puede tomar diversos formatos. Por ejemplo, las cadenas siguientes contienen formatos de fecha y hora aceptables:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

El ID. de configuración regional también afectará a si el formato de la cadena es aceptable para la conversión a un valor de fecha y hora.

En el caso de VAR_DATEVALUEONLY, el valor de hora se establece en Time 0 o medianoche. En el caso de VAR_TIMEVALUEONLY, el valor de fecha se establece en Date 0, es decir, el 30 de diciembre de 1899.

Si la cadena no se pudo convertir en un valor de fecha y hora, o si se produjo un desbordamiento numérico, el estado `COleDateTime` de este objeto no es válido.

Para obtener más información sobre los límites y la implementación `COleDateTime` de los valores, vea [el artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

##  <a name="setdate"></a>COleDateTime:: SetDate

Establece la fecha de este `COleDateTime` objeto.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parámetros

*nYear*, *nMonth*, *ndía*<br/>
Indicar los componentes de fecha que se van a `COleDateTime` copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de este `COleDateTime` objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se basa en `DateTimeStatus` el tipo enumerado. Para obtener más información, vea la función miembro [SetStatus](#setstatus) .

### <a name="remarks"></a>Comentarios

La fecha se establece en los valores especificados. La hora se establece en hora 0, medianoche.

Vea la tabla siguiente para obtener los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*Ndía*|0 - 31|

Si se desborda el día del mes, se convierte al día correcto del mes siguiente y el mes y/o año se incrementan en consecuencia. Un valor de Day de cero indica el último día del mes anterior. El comportamiento es el mismo que `SystemTimeToVariantTime`el de.

Si el valor de fecha especificado por los parámetros no es válido, el estado de este objeto se establece `COleDateTime::invalid`en. Debe usar [getStatus](#getstatus) para comprobar la validez del `DATE` valor y no debe suponer que el valor de [m_dt](#m_dt) se mantendrá sin modificar.

Estos son algunos ejemplos de valores de fecha:

|*nYear*|*nMonth*|*Ndía*|Valor|
|-------------|--------------|------------|-----------|
|2000|2|29|29 de febrero de 2000|
|1776|7|4|4 de julio de 1776|
|1925|4|35|35 de abril de 1925 (fecha no válida)|
|10000|1|1|1 de enero 10000 (fecha no válida)|

Para establecer la fecha y la hora, consulte [COleDateTime:: SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultan el `COleDateTime` valor de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>COleDateTime:: SetDateTime

Establece la fecha y hora de este `COleDateTime` objeto.

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

*nYear*, *nMonth*, *ndía*, *Nhora*, *nmín.* , *nSec*<br/>
Indicar los componentes de fecha y hora que se van a `COleDateTime` copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de este `COleDateTime` objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se basa en `DateTimeStatus` el tipo enumerado. Para obtener más información, vea la función miembro [SetStatus](#setstatus) .

### <a name="remarks"></a>Comentarios

Vea la tabla siguiente para obtener los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*Ndía*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si se desborda el día del mes, se convierte al día correcto del mes siguiente y el mes y/o año se incrementan en consecuencia. Un valor de Day de cero indica el último día del mes anterior. El comportamiento es el mismo que el de [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si el valor de fecha u hora especificado por los parámetros no es válido, el estado de este objeto se establece en no válido y no se cambia el valor de este objeto.

Estos son algunos ejemplos de valores de tiempo:

|*nHour*|*nMin*|*nSec*|Value|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válido|
|9|60|0|No válido|

Estos son algunos ejemplos de valores de fecha:

|*nYear*|*nMonth*|*Ndía*|Valor|
|-------------|--------------|------------|-----------|
|1995|4|15|15 de abril de 1995|
|1789|7|14|17 de julio de 1789|
|1925|2|30|No válido|
|10000|1|1|No válido|

Para establecer solo la fecha, consulte [COleDateTime:: SetDate](#setdate). Para establecer solo la hora, vea [COleDateTime:: setTime](#settime).

Para obtener información sobre las funciones miembro que consultan el `COleDateTime` valor de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getStatus](#getstatus).

##  <a name="setstatus"></a>  COleDateTime::SetStatus

Establece el estado de este `COleDateTime` objeto.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parámetros

*status*<br/>
Nuevo valor de estado de este `COleDateTime` objeto.

### <a name="remarks"></a>Comentarios

El valor del parámetro status se define `DateTimeStatus` mediante el tipo enumerado, que se define `COleDateTime` en la clase. Consulte [COleDateTime:: getStatus](#getstatus) para obtener más información.

> [!CAUTION]
>  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se suele usar para establecer el estado en **null** o **no válido**. El operador de asignación ([Operator =](#operator_eq)) y [SetDateTime](#setdatetime) establecen el estado del objeto basándose en los valores de origen.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getStatus](#getstatus).

##  <a name="settime"></a>COleDateTime:: SetTime

Establece la hora de este `COleDateTime` objeto.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parámetros

*nHour*, *nMin*, *nSec*<br/>
Indicar los componentes de hora que se van a `COleDateTime` copiar en este objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de este `COleDateTime` objeto se estableció correctamente; de lo contrario, 1. Este valor devuelto se basa en `DateTimeStatus` el tipo enumerado. Para obtener más información, vea la función miembro [SetStatus](#setstatus) .

### <a name="remarks"></a>Comentarios

La hora se establece en los valores especificados. La fecha se establece en la fecha 0, es decir, el 30 de diciembre de 1899.

Vea la tabla siguiente para obtener los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si el valor de hora especificado por los parámetros no es válido, el estado de este objeto se establece en no válido y no se cambia el valor de este objeto.

Estos son algunos ejemplos de valores de tiempo:

|*nHour*|*nMin*|*nSec*|Valor|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válido|
|9|60|0|No válido|

Para establecer la fecha y la hora, consulte [COleDateTime:: SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultan el `COleDateTime` valor de este objeto, vea las siguientes funciones miembro:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información sobre los límites de `COleDateTime` los valores, vea el [artículo fecha y hora: Compatibilidad con](../../atl-mfc-shared/date-and-time-automation-support.md)la automatización.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [SetDate](#setdate).

## <a name="see-also"></a>Vea también

[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[CTime (clase)](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan (clase)](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
