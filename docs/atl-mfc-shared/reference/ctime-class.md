---
title: Clase CTime
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317572"
---
# <a name="ctime-class"></a>Clase CTime

Representa una hora y una fecha absolutas.

## <a name="syntax"></a>Sintaxis

```
class CTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTime::CTime](#ctime)|Construye `CTime` objetos de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTime::Formato](#format)|Convierte un `CTime` objeto en una cadena con formato, en función de la zona horaria local.|
|[CTime::FormatGmt](#formatgmt)|Convierte un `CTime` objeto en una cadena con formato, basada en UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Convierte la información de `CTime` tiempo almacenada en el objeto en una estructura DBTIMESTAMP compatible con Win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Convierte la información de `CTime` tiempo almacenada en el objeto en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.|
|[CTime::GetCurrentTime](#getcurrenttime)|Crea `CTime` un objeto que representa la hora actual (función miembro estática).|
|[CTime::GetDay](#getday)|Devuelve el día `CTime` representado por el objeto.|
|[CTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de la `CTime` semana representado por el objeto.|
|[CTime::GetGmtTm](#getgmttm)|Desglosa un `CTime` objeto en componentes, en función de UTC.|
|[CTime::GetHour](#gethour)|Devuelve la hora representada `CTime` por el objeto.|
|[CTime::GetLocalTm](#getlocaltm)|Desglosa un `CTime` objeto en componentes, en función de la zona horaria local.|
|[CTime::GetMinute](#getminute)|Devuelve el minuto representado `CTime` por el objeto.|
|[CTime::GetMonth](#getmonth)|Devuelve el mes `CTime` representado por el objeto.|
|[CTime::GetSecond](#getsecond)|Devuelve el segundo representado `CTime` por el objeto.|
|[CTime::GetTime](#gettime)|Devuelve un **valor** __time64_t `CTime` para el objeto especificado.|
|[CTime::GetYear](#getyear)|Devuelve el año representado `CTime` por el objeto.|
|[CTime::Serialize64](#serialize64)|Serializa los datos hacia o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador + -](#operator_add_-)|Estos operadores `CTimeSpan` suman y restan y `CTime` los objetos.|
|[operador +, -](#operator_add_eq_-_eq)|Estos operadores agregan `CTimeSpan` y restan `CTime` un objeto a y desde este objeto.|
|[operador a la operadora de la red](#operator_eq)|El operador de asignación.|
|[operador, <, etc.](#ctime_comparison_operators)|Operadores de comparación.|

## <a name="remarks"></a>Observaciones

`CTime`no tiene una clase base.

`CTime`los valores se basan en la hora universal coordinada (UTC), que es equivalente a la hora universal coordinada (hora media de Greenwich, GMT). Consulte [Administración del tiempo](../../c-runtime-library/time-management.md) para obtener información sobre cómo se determina la zona horaria.

Cuando cree `CTime` un objeto, `nDST` establezca el parámetro en 0 para indicar que la hora estándar está en vigor, o en un valor mayor que 0 para indicar que el horario de verano está en vigor, o en un valor menor que cero para que el código de biblioteca en tiempo de ejecución de C calcule si el horario estándar o el horario de verano están en vigor. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) es impredecible. Si `timeptr` apunta a una estructura tm devuelta por una llamada `tm_isdst` anterior a [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), o [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), el campo contiene el valor correcto.

Una clase complementaria, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa un intervalo de tiempo.

Las `CTime` `CTimeSpan` clases y no están diseñadas para la derivación. Dado que no hay funciones `CTime` `CTimeSpan` virtuales, el tamaño y los objetos es exactamente de 8 bytes. La mayoría de las funciones miembro están en línea.

> [!NOTE]
> El límite de fecha superior es 12/31/3000. El límite inferior es 1/1/1970 12:00:00 AM GMT.

Para obtener más `CTime`información sobre el uso de , consulte los artículos [Fecha y hora](../../atl-mfc-shared/date-and-time.md)y [Administración](../../c-runtime-library/time-management.md) de tiempo en la Referencia de la biblioteca en tiempo de ejecución.

> [!NOTE]
> La `CTime` estructura cambió de MFC 7.1 a MFC 8.0. Si serializa `CTime` una estructura mediante el **operador <<** en MFC 8.0 o una versión posterior, el archivo resultante no será legible en versiones anteriores de MFC.

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>Operadores de comparación CTime

Operadores de comparación.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*time*<br/>
Objeto `CTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Estos operadores comparan dos tiempos absolutos y devuelven TRUE si la condición es true; de lo contrario FALSO.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>CTime::CTime

Crea un `CTime` nuevo objeto inicializado con la hora especificada.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Parámetros

*timeSrc*<br/>
Indica un `CTime` objeto que ya existe.

*time*<br/>
Un `__time64_t` valor de tiempo, que es el número de segundos después del 1 de enero de 1970 UTC. Tenga en cuenta que esto se ajustará a su hora local. Por ejemplo, si está en Nueva `CTime` York y crea un objeto pasando un parámetro de 0, [CTime::GetMonth](#getmonth) devolverá 12.

*nAño*, *nMes*, *nDía*, *nHour*, *nMin*, *nSec*<br/>
Indica los valores de fecha y hora `CTime` que se van a copiar en el nuevo objeto.

*nDST*<br/>
Indica si el horario de verano está en vigor. Puede tener uno de los tres valores:

- *nDST* establecido en 0La hora estándar está en vigor.

- *nDST* establecido en un valor mayor que 0El tiempo de ahorro de luz diurna está en vigor.

- *nDST* establecido en un valor menor que 0El valor predeterminado. Calcula automáticamente si la hora estándar o el horario de verano están en vigor.

*wDosDate*, *wDosTime*<br/>
Valores de fecha y hora de MS-DOS que se convertirán `CTime` en un valor de fecha y hora y se copiarán en el nuevo objeto.

*st*<br/>
Estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que se convertirá en un valor de `CTime` fecha y hora y se copiará en el nuevo objeto.

*Pies*<br/>
Estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que se convertirá en un valor de `CTime` fecha y hora y se copiará en el nuevo objeto.

*dbts*<br/>
Una referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="remarks"></a>Observaciones

Cada constructor se describe a continuación:

- `CTime();`Construye un objeto `CTime` no inicializado. Este constructor permite `CTime` definir matrices de objetos. Debe inicializar dichas matrices con tiempos válidos antes de usar.

- `CTime( const CTime& );`Construye un `CTime` objeto `CTime` a partir de otro valor.

- `CTime( __time64_t );`Construye un `CTime` objeto a partir de un tipo **de __time64_t.** Este constructor espera una hora UTC y convierte el resultado a una hora local antes de almacenar el resultado.

- `CTime( int, int, ...);`Construye un `CTime` objeto a partir de componentes de hora local con cada componente restringido a los siguientes rangos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*nAño*|1970-3000|
   |*nMes*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Este constructor realiza la conversión adecuada a UTC. La versión de depuración de la biblioteca de clases de Microsoft Foundation afirma si uno o varios de los componentes de tiempo están fuera del intervalo. Debe validar los argumentos antes de llamar. Este constructor espera una hora local.

- `CTime( WORD, WORD );`Construye un `CTime` objeto a partir de los valores de fecha y hora de MS-DOS especificados. Este constructor espera una hora local.

- `CTime( const SYSTEMTIME& );`Construye un `CTime` objeto `SYSTEMTIME` a partir de una estructura. Este constructor espera una hora local.

- `CTime( const FILETIME& );`Construye un `CTime` objeto `FILETIME` a partir de una estructura. Lo más probable `CTime FILETIME` es que no use la inicialización directamente. Si utiliza `CFile` un objeto para `CFile::GetStatus` manipular un archivo, recupera la `CTime` marca de `FILETIME` tiempo del archivo a través de un objeto inicializado con una estructura. Este constructor asume una hora basada en UTC y convierte automáticamente el valor a la hora local antes de almacenar el resultado.

   > [!NOTE]
   > El constructor `DBTIMESTAMP` using parámetro sólo está disponible cuando se incluye OLEDB.h.

Para obtener más información, vea la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK. Consulte también la entrada de fecha y hora de [MS-DOS](/windows/win32/SysInfo/ms-dos-date-and-time) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>CTime::Formato

Llame a esta función miembro para crear una representación con formato del valor de fecha y hora.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena de formato `printf` similar a la cadena de formato. Los códigos de formato,`%`precedidos por un `CTime` signo de porcentaje ( ), se reemplazan por el componente correspondiente. Otros caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. Consulte la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener una lista de códigos de formato.

*nFormatID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Observaciones

Si el estado `CTime` de este objeto es null, el valor devuelto es una cadena vacía.

Este método produce una excepción si el valor de fecha y hora al formato no va desde la medianoche, 1 de enero de 1970 hasta el 31 de diciembre de 3000 Hora coordinada universal (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>CTime::FormatGmt

Genera una cadena con formato `CTime` que corresponde a este objeto.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Especifica una cadena de `printf` formato similar a la cadena de formato. Consulte la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener más información.

*nFormatID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Observaciones

El valor de tiempo no se convierte y, por lo tanto, refleja UTC.

Este método produce una excepción si el valor de fecha y hora al formato no va desde la medianoche, 1 de enero de 1970 hasta el 31 de diciembre de 3000 Hora coordinada universal (UTC).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CTime::Format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>CTime::GetAsDBTIMESTAMP

Llame a esta función miembro para `CTime` convertir la información de tiempo almacenada en el objeto en una estructura DBTIMESTAMP compatible con Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parámetros

*dbts*<br/>
Una referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Almacena el tiempo resultante en la estructura *dbts* a la que se hace referencia. La `DBTIMESTAMP` estructura de datos inicializada `fraction` por esta función tendrá su miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>CTime::GetAsSystemTime

Llame a esta función miembro para `CTime` convertir la información de tiempo almacenada en el objeto en un [estructura SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
Una referencia a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contendrá `CTime` el valor de fecha y hora convertido del objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

`GetAsSystemTime`almacena el tiempo resultante en la estructura *timeDest* a la que se hace referencia. La `SYSTEMTIME` estructura de datos inicializada `wMilliseconds` por esta función tendrá su miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>CTime::GetCurrentTime

Devuelve `CTime` un objeto que representa la hora actual.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve la fecha y hora actual del sistema en hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>CTime::GetDay

Devuelve el día `CTime` representado por el objeto.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día del mes, según la hora local, en el intervalo del 1 al 31.

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>CTime::GetDayOfWeek

Devuelve el día de la `CTime` semana representado por el objeto.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día de la semana en función de la hora local; 1o Domingo, 2o Lunes, a 7o Sábado.

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>CTime::GetGmtTm

Obtiene un **struct tm** que contiene una descomposición del `CTime` tiempo contenido en este objeto.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Ptm*<br/>
Apunta a un búfer que recibirá los datos de tiempo. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a una estructura rellenada **tm** tal como se define en el archivo de inclusión TIME. H. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para el diseño de la estructura.

### <a name="remarks"></a>Observaciones

`GetGmtTm`devuelve UTC.

*ptm* no puede ser NULL. Si desea volver al comportamiento anterior, en el que *ptm* podría ser NULL para indicar que se debe usar un búfer interno asignado estáticamente y, a continuación, anular la definición _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>CTime::GetHour

Devuelve la hora representada `CTime` por el objeto.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la hora, según la hora local, en el intervalo de 0 a 23.

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>CTime::GetLocalTm

Obtiene una **estructura tm** que contiene una descomposición `CTime` del tiempo contenido en este objeto.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Ptm*<br/>
Apunta a un búfer que recibirá los datos de tiempo. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a una estructura rellenada **tm** tal como se define en el archivo de inclusión TIME. H. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para el diseño de la estructura.

### <a name="remarks"></a>Observaciones

`GetLocalTm`devuelve la hora local.

*ptm* no puede ser NULL. Si desea volver al comportamiento anterior, en el que *ptm* podría ser NULL para indicar que se debe usar un búfer interno asignado estáticamente y, a continuación, anular la definición _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>CTime::GetMinute

Devuelve el minuto representado `CTime` por el objeto.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el minuto, según la hora local, en el intervalo de 0 a 59.

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a>CTime::GetMonth

Devuelve el mes `CTime` representado por el objeto.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el mes, según la hora local, en el intervalo del 1 al 12 (1 de enero).

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a>CTime::GetSecond

Devuelve el segundo representado `CTime` por el objeto.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el segundo, según la hora local, en el intervalo de 0 a 59.

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a>CTime::GetTime

Devuelve un **valor** __time64_t `CTime` para el objeto especificado.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

`GetTime`devolverá el número de `CTime` segundos entre el objeto actual y el 1 de enero de 1970.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>CTime::GetYear

Devuelve el año representado `CTime` por el objeto.

```
int GetYear();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el año, según la hora local, en el intervalo 1 de enero de 1970, al 18 de enero de 2038 (incluido).

### <a name="remarks"></a>Observaciones

Esta función llama `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a llamadas a otras `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>CTime::operador ?

El operador de asignación.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parámetros

*time*<br/>
El nuevo valor de fecha y hora.

### <a name="return-value"></a>Valor devuelto

El `CTime` objeto actualizado.

### <a name="remarks"></a>Observaciones

Este operador de asignación sobrecargado `CTime` copia el tiempo de origen en este objeto. El almacenamiento de `CTime` tiempo interno en un objeto es independiente de la zona horaria. La conversión de zona horaria no es necesaria durante la asignación.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::operador +, -

Estos operadores `CTimeSpan` suman y restan y `CTime` los objetos.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*Timespan*<br/>
Objeto `CTimeSpan` que se va a agregar o restar.

*time*<br/>
El `CTime` objeto que se va a restar.

### <a name="return-value"></a>Valor devuelto

Un `CTime` `CTimeSpan` objeto que representa el resultado de la operación.

### <a name="remarks"></a>Observaciones

`CTime`objetos representan `CTimeSpan` el tiempo absoluto, los objetos representan el tiempo relativo. Los dos primeros operadores permiten `CTimeSpan` agregar y `CTime` restar objetos a y desde objetos. El tercer operador permite `CTime` restar un objeto `CTimeSpan` de otro para producir un objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>CTime::operador +-, --

Estos operadores agregan `CTimeSpan` y restan `CTime` un objeto a y desde este objeto.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto `CTimeSpan` que se va a agregar o restar.

### <a name="return-value"></a>Valor devuelto

El `CTime` objeto actualizado.

### <a name="remarks"></a>Observaciones

Estos operadores permiten agregar `CTimeSpan` y restar `CTime` un objeto a y desde este objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>CTime::Serialize64

> [!NOTE]
> Este método solo está disponible en proyectos MFC.

Serializa los datos asociados con la variable miembro a o desde un archivo.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
El `CArchive` objeto que desea actualizar.

### <a name="return-value"></a>Valor devuelto

El `CArchive` objeto actualizado.

## <a name="see-also"></a>Consulte también

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Clase CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
