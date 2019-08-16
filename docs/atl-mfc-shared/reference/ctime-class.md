---
title: CTime (clase)
ms.date: 10/18/2018
f1_keywords:
- CTime
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
ms.openlocfilehash: daf2a0d884a6b7a74b5edde2ed7db3b6aeea368d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491572"
---
# <a name="ctime-class"></a>CTime (clase)

Representa una fecha y hora absolutas.

## <a name="syntax"></a>Sintaxis

```
class CTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTime::CTime](#ctime)|`CTime` Construye objetos de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTime::Format](#format)|Convierte un `CTime` objeto en una cadena con formato, basándose en la zona horaria local.|
|[CTime::FormatGmt](#formatgmt)|Convierte un `CTime` objeto en una cadena con formato, en función de la hora UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Convierte la información de hora almacenada en `CTime` el objeto en una estructura DBTIMESTAMP compatible con Win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Convierte la información de hora almacenada en `CTime` el objeto en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.|
|[CTime::GetCurrentTime](#getcurrenttime)|Crea un `CTime` objeto que representa la hora actual (función miembro estática).|
|[CTime::GetDay](#getday)|Devuelve el día que representa el `CTime` objeto.|
|[CTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de la semana representado por el `CTime` objeto.|
|[CTime::GetGmtTm](#getgmttm)|Divide un objeto `CTime` en componentes, en función de la hora UTC.|
|[CTime::GetHour](#gethour)|Devuelve la hora representada `CTime` por el objeto.|
|[CTime::GetLocalTm](#getlocaltm)|Divide un `CTime` objeto en componentes, en función de la zona horaria local.|
|[CTime::GetMinute](#getminute)|Devuelve el minuto representado por el `CTime` objeto.|
|[CTime::GetMonth](#getmonth)|Devuelve el mes representado por el `CTime` objeto.|
|[CTime::GetSecond](#getsecond)|Devuelve el segundo representado por el `CTime` objeto.|
|[CTime::GetTime](#gettime)|Devuelve un valor de **__time64_t** para el `CTime` objeto especificado.|
|[CTime::GetYear](#getyear)|Devuelve el año representado por el `CTime` objeto.|
|[CTime::Serialize64](#serialize64)|Serializa datos a o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador +-](#operator_add_-)|Estos operadores agregan y `CTimeSpan` restan y `CTime` objetos.|
|[operator +=, -=](#operator_add_eq_-_eq)|Estos operadores agregan y restann un `CTimeSpan` objeto a y desde este `CTime` objeto.|
|[operador =](#operator_eq)|Operador de asignación.|
|[operador = =, <, etc.](#ctime_comparison_operators)|Operadores de comparación.|

## <a name="remarks"></a>Comentarios

`CTime`no tiene una clase base.

`CTime`los valores se basan en la hora universal coordinada (UTC), que es equivalente a la hora universal coordinada (hora del meridiano de Greenwich, GMT). Consulte [Administración del tiempo](../../c-runtime-library/time-management.md) para obtener información sobre cómo se determina la zona horaria.

Al crear un `CTime` objeto, establezca el parámetro `nDST` en 0 para indicar que la hora estándar está en vigor, o en un valor mayor que 0 para indicar que el horario de verano está en vigor, o en un valor menor que cero para que el proceso de código de la biblioteca en tiempo de ejecución de C e si está vigente la hora estándar o el horario de verano. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) es imprevisible. Si `timeptr` apunta a una estructura TM devuelta por una llamada anterior a [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)o [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), el `tm_isdst` campo contiene el valor correcto.

Una clase complementaria, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa un intervalo de tiempo.

Las `CTime` clases `CTimeSpan` y no están diseñadas para la derivación. Dado que no hay ninguna función virtual, el tamaño `CTime` de `CTimeSpan` los objetos y es exactamente de 8 bytes. La mayoría de las funciones miembro están alineadas.

> [!NOTE]
>  El límite de fecha superior es 12/31/3000. El límite inferior es 1/1/1970 12:00:00 AM GMT.

Para obtener más información sobre `CTime`el uso de, vea los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [Administración de tiempo](../../c-runtime-library/time-management.md) en la referencia de la biblioteca en tiempo de ejecución.

> [!NOTE]
>  La `CTime` estructura cambió de MFC 7,1 a MFC 8,0. Si serializa una `CTime` estructura mediante el **operador < <** en MFC 8,0 o una versión posterior, el archivo resultante no se podrá leer en versiones anteriores de MFC.

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

Crea un nuevo `CTime` objeto inicializado con la hora especificada.

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
Un `__time64_t` valor de hora, que es el número de segundos después del 1 de enero de 1970 UTC. Tenga en cuenta que esto se ajustará a la hora local. Por ejemplo, si está en Nueva York y crea un `CTime` objeto pasando un parámetro de 0, [ctime:: getMonth](#getmonth) devolverá 12.

*nYear*, *nMonth*, *ndía*, *Nhora*, *nmín.* , *nSec*<br/>
Indica los valores de fecha y hora que se van a copiar `CTime` en el nuevo objeto.

*nDST*<br/>
Indica si el horario de verano está en vigor. Puede tener uno de estos tres valores:

- el valor de *nDST* establecido en 0Standard está en vigor.

- el valor de *nDST* establecido en un valor mayor que 0Daylight de tiempo de ahorro está en vigor.

- *nDST* se establece en un valor menor que 0The predeterminado. Calcula automáticamente si está vigente la hora estándar o el horario de verano.

*wDosDate*, *wDosTime*<br/>
Valores de fecha y hora de ms-dos que se convertirán en un valor de fecha y hora y `CTime` se copiarán en el nuevo objeto.

*st*<br/>
Estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que se va a convertir en un valor de fecha y hora y copiarse `CTime` en el nuevo objeto.

*ft*<br/>
Una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que se va a convertir en un valor de fecha y hora y copiarse en el nuevo `CTime` objeto.

*dbts*<br/>
Referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="remarks"></a>Comentarios

A continuación se describe cada constructor:

- `CTime();`Construye un `CTime` objeto no inicializado. Este constructor permite definir `CTime` matrices de objetos. Debe inicializar dichas matrices con horas válidas antes de usar.

- `CTime( const CTime& );`Construye un `CTime` objeto a partir de `CTime` otro valor.

- `CTime( __time64_t );`Construye un `CTime` objeto a partir de un tipo **__time64_t** . Este constructor espera una hora UTC y convierte el resultado en una hora local antes de almacenar el resultado.

- `CTime( int, int, ...);`Construye un `CTime` objeto a partir de los componentes de hora local con cada componente restringido a los siguientes intervalos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*Ndía*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Este constructor hace que la conversión correspondiente sea la hora UTC. La versión de depuración del biblioteca MFC valida si uno o varios de los componentes de hora están fuera del intervalo. Debe validar los argumentos antes de llamar a. Este constructor espera una hora local.

- `CTime( WORD, WORD );`Construye un `CTime` objeto a partir de los valores de fecha y hora de ms-dos especificados. Este constructor espera una hora local.

- `CTime( const SYSTEMTIME& );`Construye un `CTime` objeto a partir de `SYSTEMTIME` una estructura. Este constructor espera una hora local.

- `CTime( const FILETIME& );`Construye un `CTime` objeto a partir de `FILETIME` una estructura. Lo más probable es que no `CTime FILETIME` se use la inicialización directamente. Si usa un `CFile` objeto para manipular un archivo, `CFile::GetStatus` recupera la marca de tiempo de archivo automáticamente a través de un `CTime` objeto inicializado con una `FILETIME` estructura. Este constructor supone un tiempo basado en UTC y convierte automáticamente el valor a la hora local antes de almacenar el resultado.

   > [!NOTE]
   > El constructor que `DBTIMESTAMP` usa el parámetro solo está disponible cuando se incluye OleDb. h.

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
Cadena de formato similar a la `printf` cadena de formato. Los códigos de formato, precedidos por`%`un signo de porcentaje (), se `CTime` reemplazan por el componente correspondiente. Los demás caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. Vea la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener una lista de códigos de formato.

*nFormatID*<br/>
IDENTIFICADOR de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Comentarios

Si el estado de este `CTime` objeto es null, el valor devuelto es una cadena vacía.

Este método produce una excepción si el valor de fecha y hora que se va a dar formato no abarca desde la medianoche del 1 de enero de 1970 hasta el 31 de diciembre de 3000 de la hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

Genera una cadena con formato que corresponde a `CTime` este objeto.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Especifica una cadena de formato similar a `printf` la cadena de formato. Vea la función en tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener más información.

*nFormatID*<br/>
IDENTIFICADOR de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

[CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Comentarios

El valor de hora no se convierte y, por tanto, refleja la hora UTC.

Este método produce una excepción si el valor de fecha y hora que se va a dar formato no abarca desde la medianoche del 1 de enero de 1970 hasta el 31 de diciembre de 3000 de la hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [ctime:: Format](#format).

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

Llame a esta función miembro para convertir la información de hora almacenada en el `CTime` objeto en una estructura DBTIMESTAMP compatible con Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parámetros

*dbts*<br/>
Referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Almacena el tiempo resultante en la estructura *DBTS* a la que se hace referencia. La `DBTIMESTAMP` estructura de datos inicializada por esta función tendrá su `fraction` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

Llame a esta función miembro para convertir la información de hora almacenada en el `CTime` objeto en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible con Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
Referencia a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contendrá el valor de fecha y hora convertido del `CTime` objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`GetAsSystemTime`almacena el tiempo resultante en la estructura *timeDest* a la que se hace referencia. La `SYSTEMTIME` estructura de datos inicializada por esta función tendrá su `wMilliseconds` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

Devuelve un `CTime` objeto que representa la hora actual.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Comentarios

Devuelve la fecha y hora actuales del sistema en hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>CTime:: getDay (

Devuelve el día que representa el `CTime` objeto.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día del mes, en función de la hora local, en el intervalo comprendido entre 1 y 31.

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

Devuelve el día de la semana representado por el `CTime` objeto.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día de la semana basándose en la hora local; 1 = Domingo, 2 = lunes, a 7 = sábado.

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

Obtiene un **struct TM** que contiene una descomposición de la hora contenida en `CTime` este objeto.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*ptm*<br/>
Señala a un búfer que recibirá los datos de hora. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un **struct de estructura rellena TM** tal y como se define en la hora de inclusión del archivo. C. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para ver el diseño de la estructura.

### <a name="remarks"></a>Comentarios

`GetGmtTm`Devuelve la hora UTC.

*PTM* no puede ser null. Si desea revertir al comportamiento anterior, en el que *PTM* podría ser null para indicar que se debe usar un búfer interno asignado estáticamente y, después, anular la definición de _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

Devuelve la hora representada `CTime` por el objeto.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la hora, en función de la hora local, en el intervalo comprendido entre 0 y 23.

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

Obtiene un **struct TM** que contiene una descomposición de la hora contenida `CTime` en este objeto.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*ptm*<br/>
Señala a un búfer que recibirá los datos de hora. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un **struct de estructura rellena TM** tal y como se define en la hora de inclusión del archivo. C. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para ver el diseño de la estructura.

### <a name="remarks"></a>Comentarios

`GetLocalTm`Devuelve la hora local.

*PTM* no puede ser null. Si desea revertir al comportamiento anterior, en el que *PTM* podría ser null para indicar que se debe usar un búfer interno asignado estáticamente y, después, anular la definición de _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>CTime:: GetMinute

Devuelve el minuto representado por el `CTime` objeto.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el minuto, en función de la hora local, en el intervalo comprendido entre 0 y 59.

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getmonth"></a>CTime:: GetMonth

Devuelve el mes representado por el `CTime` objeto.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el mes, en función de la hora local, en el intervalo de 1 a 12 (1 = enero).

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [getDay (](#getday).

##  <a name="getsecond"></a>  CTime::GetSecond

Devuelve el segundo representado por el `CTime` objeto.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el segundo, en función de la hora local, en el intervalo comprendido entre 0 y 59.

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="gettime"></a>  CTime::GetTime

Devuelve un valor de **__time64_t** para el `CTime` objeto especificado.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

`GetTime`devolverá el número de segundos entre el `CTime` objeto actual y el 1 de enero de 1970.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

Devuelve el año representado por el `CTime` objeto.

```
int GetYear();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el año, en función de la hora local, en el intervalo del 1 de enero de 1970 al 18 de enero de 2038 (inclusivo).

### <a name="remarks"></a>Comentarios

Esta función llama `GetLocalTm`a, que usa un búfer interno asignado estáticamente. Los datos de este búfer se sobrescriben debido a las llamadas a `CTime` otras funciones miembro.

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

Objeto actualizado `CTime` .

### <a name="remarks"></a>Comentarios

Este operador de asignación sobrecargado copia la hora de origen `CTime` en este objeto. El almacenamiento de hora interno en `CTime` un objeto es independiente de la zona horaria. La conversión de zona horaria no es necesaria durante la asignación.

##  <a name="operator_add_-"></a>CTime:: Operator +,-

Estos operadores agregan y `CTimeSpan` restan y `CTime` objetos.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*timeSpan*<br/>
`CTimeSpan` Objeto que se va a agregar o sustraer.

*time*<br/>
`CTime` Objeto que se va a restar.

### <a name="return-value"></a>Valor devuelto

Objeto `CTime` o`CTimeSpan` que representa el resultado de la operación.

### <a name="remarks"></a>Comentarios

`CTime`los objetos representan el tiempo `CTimeSpan` absoluto, los objetos representan el tiempo relativo. Los dos primeros operadores permiten agregar y restar `CTimeSpan` objetos a y desde `CTime` objetos. El tercer operador permite restar un `CTime` objeto de otro para producir un `CTimeSpan` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>CTime:: Operator + =,-=

Estos operadores agregan y restann un `CTimeSpan` objeto a y desde este `CTime` objeto.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
`CTimeSpan` Objeto que se va a agregar o sustraer.

### <a name="return-value"></a>Valor devuelto

Objeto actualizado `CTime` .

### <a name="remarks"></a>Comentarios

Estos operadores permiten agregar y restar un `CTimeSpan` objeto a y desde este `CTime` objeto.

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

*ar*<br/>
`CArchive` Objeto que se desea actualizar.

### <a name="return-value"></a>Valor devuelto

Objeto actualizado `CArchive` .

## <a name="see-also"></a>Vea también

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan (clase)](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
