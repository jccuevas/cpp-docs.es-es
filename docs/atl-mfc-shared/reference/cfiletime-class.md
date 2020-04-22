---
title: Clase CFileTime
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: fd19d941365c7772363417ce3e9225bd9b0300b2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748842"
---
# <a name="cfiletime-class"></a>Clase CFileTime

Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.

## <a name="syntax"></a>Sintaxis

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Llame a esta función estática para recuperar un `CFileTime` objeto que representa la fecha y hora actuales del sistema.|
|[CFileTime::GetTime](#gettime)|Llame a este método para `CFileTime` recuperar la hora del objeto.|
|[CFileTime::LocalToUTC](#localtoutc)|Llame a este método para convertir una hora de archivo local en una hora de archivo basada en la hora universal coordinada (UTC).|
|[CFileTime::SetTime](#settime)|Llame a este método para establecer `CFileTime` la fecha y hora almacenadas por el objeto.|
|[CFileTime::UTCToLocal](#utctolocal)|Llame a este método para convertir el tiempo en función de la hora universal coordinada (UTC) a la hora de archivo local.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTime::operador -](#operator_-)|Este operador se utiliza para `CFileTime` realizar `CFileTimeSpan` restas en un objeto u.|
|[CFileTime::operator !o](#operator_neq)|Este operador compara `CFileTime` dos objetos para la desigualdad.|
|[CFileTime::operador +](#operator_add)|Este operador se usa para sumar en un objeto `CFileTimeSpan`.|
|[CFileTime::operador +o](#operator_add_eq)|Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.|
|[CFileTime::operator&lt;](#operator_lt)|Este operador compara dos objetos `CFileTime` para determinar el menor.|
|[CFileTime::operator&lt;=](#operator_lt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.|
|[CFileTime::operator ?](#operator_eq)|El operador de asignación.|
|[CFileTime::operador --](#operator_-_eq)|Este operador se utiliza para `CFileTimeSpan` realizar la resta en un objeto y asignar el resultado al objeto actual.|
|[CFileTime::operador ?](#operator_eq_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales.|
|[CFileTime::operator&gt;](#operator_gt)|Este operador compara dos objetos `CFileTime` para determinar el mayor.|
|[CFileTime::operator&gt;=](#operator_gt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[CFileTime::Day](#day)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un día.|
|[CFileTime::Hora](#hour)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen una hora.|
|[CFileTime::Millisecond](#millisecond)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un milisegundo.|
|[CFileTime::Minute](#minute)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un minuto.|
|[CFileTime::Segundo](#second)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un segundo.|
|[CFileTime::Semana](#week)|Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen una semana.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para administrar los valores de fecha y hora asociados con la creación, el acceso y la modificación de archivos. Los métodos y datos de esta clase `CFileTimeSpan` se utilizan con frecuencia junto con los objetos, que tratan con valores de tiempo relativos.

El valor de fecha y hora se almacena como un valor de 64 bits que representa el número de intervalos de 100 nanosegundos desde el 1 de enero de 1601. Este es el formato de hora universal coordinada (UTC).

Se proporcionan las siguientes variables miembro const estáticas para simplificar los cálculos:

|Variable miembro|Número de intervalos de 100 nanosegundos|
|---------------------|-----------------------------------------|
|Millisecond|10 000|
|Segundo|Milisegundo \* 1.000|
|Minute|Segundo \* 60|
|Hour|Minuto \* 60|
|Día|Hora \* 24|
|Semana|Día \* 7|

**Nota** No todos los sistemas de archivos pueden registrar la creación y la última hora de acceso y no todos los sistemas de archivos los registran de la misma manera. Por ejemplo, en el sistema de archivos FAT de Windows NT, el tiempo de creación tiene una resolución de 10 milisegundos, el tiempo de escritura tiene una resolución de 2 segundos y el tiempo de acceso tiene una resolución de 1 día (la fecha de acceso). En NTFS, el tiempo de acceso tiene una resolución de 1 hora. Además, FAT registra las horas en el disco en la hora local, pero NTFS registra las horas en el disco en UTC. Para obtener más información, consulte [Tiempos de archivo](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>CFileTime::CFileTime

El constructor.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Una estructura [FILETIME.](/windows/win32/api/minwinbase/ns-minwinbase-filetime)

*Ntime*<br/>
La fecha y la hora expresadas como un valor de 64 bits.

### <a name="remarks"></a>Observaciones

El `CFileTime` objeto se puede crear utilizando `FILETIME` una fecha y hora existentes a partir de una estructura, o expresarse como un valor de 64 bits (en formatos de hora local o de hora universal coordinada (UTC)). El constructor predeterminado establece la hora en 0.

## <a name="cfiletimeday"></a><a name="day"></a>CFileTime::Day

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un día.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Llame a esta función estática para recuperar un `CFileTime` objeto que representa la fecha y hora actuales del sistema.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la fecha y hora actual del sistema en formato de hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>CFileTime::GetTime

Llame a este método para `CFileTime` recuperar la hora del objeto.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la fecha y la hora como un número de 64 bits, que puede estar en formato local o de hora universal coordinada (UTC).

## <a name="cfiletimehour"></a><a name="hour"></a>CFileTime::Hora

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen una hora.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>CFileTime::LocalToUTC

Llame a este método para convertir una hora de archivo local en una hora de archivo basada en la hora universal coordinada (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTime` un objeto que contiene la hora en formato UTC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::UTCToLocal](#utctolocal).

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>CFileTime::Millisecond

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un milisegundo.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>CFileTime::Minute

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un minuto.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>CFileTime::operador -

Este operador se utiliza para `CFileTime` realizar `CFileTimeSpan` restas en un objeto u.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto `CFileTimeSpan` .

*Pies*<br/>
Objeto `CFileTime` .

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTime` un objeto `CFileTimeSpan` o un objeto que representa el resultado de la diferencia de tiempo entre los dos objetos.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>CFileTime::operator !o

Este operador compara `CFileTime` dos objetos para la desigualdad.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CFileTime` se compara no es igual al objeto, de lo contrario FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>CFileTime::operador +

Este operador se usa para sumar en un objeto `CFileTimeSpan`.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTime` un objeto que representa el resultado de la hora original más un tiempo relativo.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>CFileTime::operador +o

Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTime` objeto actualizado, que representa el resultado de la hora original más un tiempo relativo.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>CFileTime::operator&lt;

Este operador compara dos objetos `CFileTime` para determinar el menor.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor (antes en el tiempo) que el segundo, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>CFileTime::operator&lt;=

Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que (antes en el tiempo) o igual que el segundo, de lo contrario FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>CFileTime::operator ?

El operador de asignación.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que contiene la nueva hora y fecha.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTime` objeto actualizado.

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>CFileTime::operador --

Este operador se utiliza para `CFileTimeSpan` realizar la resta en un objeto y asignar el resultado al objeto actual.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto `CFileTimeSpan` que contiene el tiempo relativo que se va a restar.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTime` objeto actualizado.

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>CFileTime::operador ?

Este operador compara dos objetos `CFileTime` para determinar si son iguales.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
El objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales, de lo contrario FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>CFileTime::operator&gt;

Este operador compara dos objetos `CFileTime` para determinar el mayor.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (más adelante en el tiempo) que el segundo, en caso de no FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>CFileTime::operator&gt;=

Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*Pies*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (más adelante en el tiempo) o igual que el segundo, de lo contrario FALSE.

## <a name="cfiletimesecond"></a><a name="second"></a>CFileTime::Segundo

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen un día.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimesettime"></a><a name="settime"></a>CFileTime::SetTime

Llame a este método para establecer `CFileTime` la fecha y hora almacenadas por el objeto.

```cpp
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parámetros

*Ntime*<br/>
El valor de 64 bits que representa la fecha y la hora, en formato local o de hora universal coordinada (UTC).

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>CFileTime::UTCToLocal

Llame a este método para convertir el tiempo en función de la hora universal coordinada (UTC) a la hora de archivo local.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTime` un objeto que contiene la hora en formato de hora de archivo local.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>CFileTime::Semana

Un miembro de datos estáticos que almacena el número de intervalos de 100 nanosegundos que componen una semana.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](#millisecond).

## <a name="see-also"></a>Vea también

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[Clase CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
