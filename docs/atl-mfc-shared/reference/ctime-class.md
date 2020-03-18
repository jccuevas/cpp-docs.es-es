---
title: CTime (clase)
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
ms.openlocfilehash: a1d62cca42e3110974b07dae143bafcf807fed7e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440487"
---
# <a name="ctime-class"></a>CTime (clase)

Representa una fecha y hora absolutas.

## <a name="syntax"></a>Sintaxis

```
class CTime
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTime:: CTime](#ctime)|Construye objetos `CTime` de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTime:: Format](#format)|Convierte un objeto `CTime` en una cadena con formato, basándose en la zona horaria local.|
|[CTime:: FormatGmt](#formatgmt)|Convierte un objeto `CTime` en una cadena con formato, según la hora UTC.|
|[CTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|Convierte la información de hora almacenada en el objeto `CTime` en una estructura DBTIMESTAMP compatible con Win32.|
|[CTime:: GetAsSystemTime](#getassystemtime)|Convierte la información de hora almacenada en el objeto `CTime` en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.|
|[CTime:: GetCurrentTime](#getcurrenttime)|Crea un objeto `CTime` que representa la hora actual (función miembro estática).|
|[CTime:: getDay (](#getday)|Devuelve el día que representa el objeto `CTime`.|
|[CTime:: GetDayOfWeek](#getdayofweek)|Devuelve el día de la semana representado por el objeto `CTime`.|
|[CTime:: GetGmtTm](#getgmttm)|Divide un objeto de `CTime` en componentes, en función de la hora UTC.|
|[CTime:: GetHour](#gethour)|Devuelve la hora representada por el objeto `CTime`.|
|[CTime:: GetLocalTm](#getlocaltm)|Divide un objeto de `CTime` en componentes, en función de la zona horaria local.|
|[CTime:: GetMinute](#getminute)|Devuelve el minuto representado por el objeto `CTime`.|
|[CTime:: GetMonth](#getmonth)|Devuelve el mes representado por el objeto `CTime`.|
|[CTime:: GetSecond](#getsecond)|Devuelve el segundo representado por el objeto `CTime`.|
|[CTime:: GetTime](#gettime)|Devuelve un valor de **__time64_t** para el objeto `CTime` especificado.|
|[CTime:: GetYear](#getyear)|Devuelve el año representado por el objeto `CTime`.|
|[CTime:: Serialize64](#serialize64)|Serializa datos a o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador +-](#operator_add_-)|Estos operadores agregan y restan `CTimeSpan` y `CTime` objetos.|
|[operador + =,-=](#operator_add_eq_-_eq)|Estos operadores agregan y restann un objeto `CTimeSpan` a este objeto `CTime` y desde este.|
|[operador =](#operator_eq)|Operador de asignación.|
|[operador = =, <, etc.](#ctime_comparison_operators)|Operadores de comparación.|

## <a name="remarks"></a>Observaciones

`CTime` no tiene una clase base.

`CTime` valores se basan en la hora universal coordinada (UTC), que es equivalente a la hora universal coordinada (hora del meridiano de Greenwich, GMT). Consulte [Administración del tiempo](../../c-runtime-library/time-management.md) para obtener información sobre cómo se determina la zona horaria.

Cuando cree un objeto de `CTime`, establezca el parámetro `nDST` en 0 para indicar que la hora estándar está en vigor, o en un valor mayor que 0 para indicar que el horario de verano está en vigor, o en un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) es imprevisible. Si `timeptr` apunta a una estructura TM devuelta por una llamada anterior a [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)o [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), el campo `tm_isdst` contiene el valor correcto.

Una clase complementaria, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa un intervalo de tiempo.

Las clases `CTime` y `CTimeSpan` no están diseñadas para la derivación. Dado que no hay ninguna función virtual, el tamaño de los objetos `CTime` y `CTimeSpan` es exactamente de 8 bytes. La mayoría de las funciones miembro están alineadas.

> [!NOTE]
>  El límite de fecha superior es 12/31/3000. El límite inferior es 1/1/1970 12:00:00 AM GMT.

Para obtener más información sobre el uso de `CTime`, vea los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [Administración de tiempo](../../c-runtime-library/time-management.md) en la referencia de la biblioteca en tiempo de ejecución.

> [!NOTE]
>  La estructura de `CTime` ha cambiado de MFC 7,1 a MFC 8,0. Si serializa una estructura de `CTime` mediante el **operador < <** en MFC 8,0 o una versión posterior, el archivo resultante no se podrá leer en versiones anteriores de MFC.

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime. h

##  <a name="ctime_comparison_operators"></a>Operadores de comparación de CTime

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

Estos operadores comparan dos horas absolutas y devuelven TRUE si la condición es true. en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>CTime:: CTime

Crea un nuevo objeto `CTime` inicializado con la hora especificada.

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
Indica un objeto de `CTime` que ya existe.

*time*<br/>
Un valor de hora de `__time64_t`, que es el número de segundos después del 1 de enero de 1970 UTC. Tenga en cuenta que esto se ajustará a la hora local. Por ejemplo, si está en Nueva York y crea un objeto `CTime` pasando un parámetro de 0, [ctime:: getMonth](#getmonth) devolverá 12.

*nYear*, *nMonth*, *ndía*, *Nhora*, *nmín.* , *nSec*<br/>
Indica los valores de fecha y hora que se van a copiar en el nuevo objeto de `CTime`.

*nDST*<br/>
Indica si el horario de verano está en vigor. Puede tener uno de estos tres valores:

- el valor de *nDST* establecido en 0Standard está en vigor.

- el valor de *nDST* establecido en un valor mayor que 0Daylight de tiempo de ahorro está en vigor.

- *nDST* se establece en un valor menor que 0The predeterminado. Calcula automáticamente si está vigente la hora estándar o el horario de verano.

*wDosDate*, *wDosTime*<br/>
Valores de fecha y hora de MS-DOS que se van a convertir en un valor de fecha y hora y copiarse en el nuevo objeto de `CTime`.

*primer*<br/>
Estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que se va a convertir en un valor de fecha y hora y copiarse en el nuevo objeto de `CTime`.

*tolerancia*<br/>
Una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que se va a convertir en un valor de fecha y hora y copiarse en el nuevo objeto `CTime`.

*DBTS*<br/>
Referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="remarks"></a>Observaciones

A continuación se describe cada constructor:

- `CTime();` construye un objeto `CTime` no inicializado. Este constructor permite definir `CTime` matrices de objetos. Debe inicializar dichas matrices con horas válidas antes de usar.

- `CTime( const CTime& );` crea un objeto `CTime` a partir de otro valor de `CTime`.

- `CTime( __time64_t );` crea un objeto `CTime` a partir de un tipo **__time64_t** . Este constructor espera una hora UTC y convierte el resultado en una hora local antes de almacenar el resultado.

- `CTime( int, int, ...);` crea un objeto `CTime` a partir de componentes de hora local con cada componente restringido a los siguientes intervalos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*Ndía*|1-31|
   |*Nhora*|0-23|
   |*Nmín.*|0-59|
   |*nSec*|0-59|

   Este constructor hace que la conversión correspondiente sea la hora UTC. La versión de depuración del biblioteca MFC valida si uno o varios de los componentes de hora están fuera del intervalo. Debe validar los argumentos antes de llamar a. Este constructor espera una hora local.

- `CTime( WORD, WORD );` crea un objeto `CTime` a partir de los valores de fecha y hora de MS-DOS especificados. Este constructor espera una hora local.

- `CTime( const SYSTEMTIME& );` crea un objeto `CTime` a partir de una estructura `SYSTEMTIME`. Este constructor espera una hora local.

- `CTime( const FILETIME& );` crea un objeto `CTime` a partir de una estructura `FILETIME`. Lo más probable es que no use la inicialización de `CTime FILETIME` directamente. Si usa un objeto de `CFile` para manipular un archivo, `CFile::GetStatus` recupera la marca de tiempo del archivo a través de un objeto `CTime` inicializado con una estructura de `FILETIME`. Este constructor supone un tiempo basado en UTC y convierte automáticamente el valor a la hora local antes de almacenar el resultado.

   > [!NOTE]
   > El constructor que usa `DBTIMESTAMP` parámetro solo está disponible cuando se incluye OLEDB. h.

Para obtener más información, vea la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) en el Windows SDK. Consulte también la entrada de [fecha y hora de ms-dos](/windows/win32/SysInfo/ms-dos-date-and-time) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>CTime:: Format

Llame a esta función miembro para crear una representación con formato del valor de fecha y hora.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena de formato similar a la cadena de formato de `printf`. Los códigos de formato, precedidos por un signo de porcentaje (`%`), se reemplazan por el componente de `CTime` correspondiente. Los demás caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. Vea la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener una lista de códigos de formato.

*nFormatID*<br/>
IDENTIFICADOR de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Observaciones

Si el estado de este objeto `CTime` es null, el valor devuelto es una cadena vacía.

Este método produce una excepción si el valor de fecha y hora que se va a dar formato no abarca desde la medianoche del 1 de enero de 1970 hasta el 31 de diciembre de 3000 de la hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>CTime:: FormatGmt

Genera una cadena con formato que corresponde a este objeto `CTime`.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Especifica una cadena de formato similar a la cadena de formato de `printf`. Vea la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener más información.

*nFormatID*<br/>
IDENTIFICADOR de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Observaciones

El valor de hora no se convierte y, por tanto, refleja la hora UTC.

Este método produce una excepción si el valor de fecha y hora que se va a dar formato no abarca desde la medianoche del 1 de enero de 1970 hasta el 31 de diciembre de 3000 de la hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [ctime:: Format](#format).

##  <a name="getasdbtimestamp"></a>CTime:: GetAsDBTIMESTAMP

Llame a esta función miembro para convertir la información de hora almacenada en el objeto `CTime` en una estructura DBTIMESTAMP compatible con Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parámetros

*DBTS*<br/>
Referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Almacena el tiempo resultante en la estructura *DBTS* a la que se hace referencia. La estructura de datos `DBTIMESTAMP` inicializada por esta función tendrá su `fraction` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>CTime:: GetAsSystemTime

Llame a esta función miembro para convertir la información de hora almacenada en el objeto `CTime` en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
Referencia a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contendrá el valor de fecha y hora convertido del objeto `CTime`.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

`GetAsSystemTime` almacena el tiempo resultante en la estructura *timeDest* a la que se hace referencia. La estructura de datos `SYSTEMTIME` inicializada por esta función tendrá su `wMilliseconds` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>CTime:: GetCurrentTime

Devuelve un objeto `CTime` que representa la hora actual.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve la fecha y hora actuales del sistema en hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>CTime:: getDay (

Devuelve el día que representa el objeto `CTime`.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día del mes, en función de la hora local, en el intervalo comprendido entre 1 y 31.

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>CTime:: GetDayOfWeek

Devuelve el día de la semana representado por el objeto `CTime`.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día de la semana basándose en la hora local; 1 = Domingo, 2 = lunes, a 7 = sábado.

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>CTime:: GetGmtTm

Obtiene un **struct TM** que contiene una descomposición de la hora contenida en este objeto `CTime`.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*PTM*<br/>
Señala a un búfer que recibirá los datos de hora. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un **struct de estructura rellena TM** tal y como se define en la hora de inclusión del archivo. C. Vea [gmtime, _gmtime32 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para ver el diseño de la estructura.

### <a name="remarks"></a>Observaciones

`GetGmtTm` devuelve la hora UTC.

*PTM* no puede ser null. Si desea revertir al comportamiento anterior, en el que *PTM* podría ser null para indicar que se debe usar un búfer interno asignado estáticamente, desdefina _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>CTime:: GetHour

Devuelve la hora representada por el objeto `CTime`.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la hora, en función de la hora local, en el intervalo comprendido entre 0 y 23.

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>CTime:: GetLocalTm

Obtiene un **struct TM** que contiene una descomposición de la hora contenida en este objeto `CTime`.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*PTM*<br/>
Señala a un búfer que recibirá los datos de hora. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un **struct de estructura rellena TM** tal y como se define en la hora de inclusión del archivo. C. Vea [gmtime, _gmtime32 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para ver el diseño de la estructura.

### <a name="remarks"></a>Observaciones

`GetLocalTm` devuelve la hora local.

*PTM* no puede ser null. Si desea revertir al comportamiento anterior, en el que *PTM* podría ser null para indicar que se debe usar un búfer interno asignado estáticamente, desdefina _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>CTime:: GetMinute

Devuelve el minuto representado por el objeto `CTime`.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el minuto, en función de la hora local, en el intervalo comprendido entre 0 y 59.

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getmonth"></a>CTime:: GetMonth

Devuelve el mes representado por el objeto `CTime`.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el mes, en función de la hora local, en el intervalo de 1 a 12 (1 = enero).

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getDay (](#getday).

##  <a name="getsecond"></a>CTime:: GetSecond

Devuelve el segundo representado por el objeto `CTime`.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el segundo, en función de la hora local, en el intervalo comprendido entre 0 y 59.

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="gettime"></a>CTime:: GetTime

Devuelve un valor de **__time64_t** para el objeto `CTime` especificado.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

`GetTime` devolverá el número de segundos entre el objeto de `CTime` actual y el 1 de enero de 1970.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>CTime:: GetYear

Devuelve el año representado por el objeto `CTime`.

```
int GetYear();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el año, en función de la hora local, en el intervalo del 1 de enero de 1970 al 18 de enero de 2038 (inclusivo).

### <a name="remarks"></a>Observaciones

Esta función llama a `GetLocalTm`, que utiliza un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a otras funciones miembro de `CTime`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getDay (](#getday).

##  <a name="operator_eq"></a>CTime:: Operator =

Operador de asignación.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parámetros

*time*<br/>
Nuevo valor de fecha y hora.

### <a name="return-value"></a>Valor devuelto

Objeto `CTime` actualizado.

### <a name="remarks"></a>Observaciones

Este operador de asignación sobrecargado copia la hora de origen en este objeto `CTime`. El almacenamiento de hora interno en un objeto `CTime` es independiente de la zona horaria. La conversión de zona horaria no es necesaria durante la asignación.

##  <a name="operator_add_-"></a>CTime:: Operator +,-

Estos operadores agregan y restan `CTimeSpan` y `CTime` objetos.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*timeSpan*<br/>
Objeto `CTimeSpan` que se va a agregar o sustraer.

*time*<br/>
Objeto de `CTime` que se va a restar.

### <a name="return-value"></a>Valor devuelto

`CTime` o `CTimeSpan` objeto que representa el resultado de la operación.

### <a name="remarks"></a>Observaciones

`CTime` objetos representan el tiempo absoluto, `CTimeSpan` objetos representan el tiempo relativo. Los dos primeros operadores permiten agregar y restar `CTimeSpan` objetos a y desde objetos `CTime`. El tercer operador permite restar un objeto `CTime` de otro para producir un objeto `CTimeSpan`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>CTime:: Operator + =,-=

Estos operadores agregan y restann un objeto `CTimeSpan` a este objeto `CTime` y desde este.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CTimeSpan` que se va a agregar o sustraer.

### <a name="return-value"></a>Valor devuelto

Objeto `CTime` actualizado.

### <a name="remarks"></a>Observaciones

Estos operadores permiten agregar y sustraer un objeto de `CTimeSpan` de este objeto `CTime`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>CTime:: Serialize64

> [!NOTE]
> Este método solo está disponible en los proyectos de MFC.

Serializa los datos asociados a la variable de miembro a o desde un archivo.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*analítico*<br/>
Objeto de `CArchive` que se desea actualizar.

### <a name="return-value"></a>Valor devuelto

Objeto `CArchive` actualizado.

## <a name="see-also"></a>Consulte también

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan (clase)](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
