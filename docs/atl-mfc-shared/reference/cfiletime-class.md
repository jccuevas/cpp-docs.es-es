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
ms.openlocfilehash: b24d1e4d3e670a820c41735617b7db6780ff137c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491481"
---
# <a name="cfiletime-class"></a>Clase CFileTime

Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.

## <a name="syntax"></a>Sintaxis

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Llame a esta función estática para recuperar `CFileTime` un objeto que represente la fecha y hora actuales del sistema.|
|[CFileTime::GetTime](#gettime)|Llame a este método para recuperar la hora del `CFileTime` objeto.|
|[CFileTime::LocalToUTC](#localtoutc)|Llame a este método para convertir una hora de archivo local en una hora de archivo basándose en la hora universal coordinada (UTC).|
|[CFileTime::SetTime](#settime)|Llame a este método para establecer la fecha y la hora almacenadas por el `CFileTime` objeto.|
|[CFileTime::UTCToLocal](#utctolocal)|Llame a este método para convertir la hora basada en la hora universal coordinada (UTC) a la hora del archivo local.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTime:: Operator-](#operator_-)|Este operador se usa para realizar la resta en un `CFileTime` objeto `CFileTimeSpan` o.|
|[CFileTime:: Operator! =](#operator_neq)|Este operador compara dos `CFileTime` objetos para determinar si no son iguales.|
|[CFileTime:: Operator +](#operator_add)|Este operador se usa para sumar en un objeto `CFileTimeSpan`.|
|[CFileTime::operator +=](#operator_add_eq)|Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.|
|[CFileTime:: Operator&lt;](#operator_lt)|Este operador compara dos objetos `CFileTime` para determinar el menor.|
|[CFileTime:: Operator&lt;=](#operator_lt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.|
|[CFileTime::operator =](#operator_eq)|Operador de asignación.|
|[CFileTime:: Operator-=](#operator_-_eq)|Este operador se usa para realizar la resta en un `CFileTimeSpan` objeto y asignar el resultado al objeto actual.|
|[CFileTime::operator ==](#operator_eq_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales.|
|[CFileTime:: Operator&gt;](#operator_gt)|Este operador compara dos objetos `CFileTime` para determinar el mayor.|
|[CFileTime:: Operator&gt;=](#operator_gt_eq)|Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.|

### <a name="public-constants"></a>Constantes públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTime::Day](#day)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un día.|
|[CFileTime::Hour](#hour)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman una hora.|
|[CFileTime::Millisecond](#millisecond)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un milisegundo.|
|[CFileTime::Minute](#minute)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un minuto.|
|[CFileTime::Second](#second)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un segundo.|
|[CFileTime::Week](#week)|Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman una semana.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a la creación, el acceso y la modificación de archivos. Los métodos y los datos de esta clase se utilizan con frecuencia junto `CFileTimeSpan` con los objetos, que se ocupan de los valores de hora relativos.

El valor de fecha y hora se almacena como un valor de 64 bits que representa el número de intervalos de 100-nanosegundos desde el 1 de enero de 1601. Este es el formato de hora universal coordinada (UTC).

Las siguientes variables miembro const estáticas se proporcionan para simplificar los cálculos:

|Variable de miembro|Número de intervalos de 100 segundos|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|Second|Milisegundo \* 1.000|
|Minute|Segundo \* 60|
|Hour|Minuto \* 60|
|Día|Hora \* 24|
|Semana|Día \* 7|

**Nota:** No todos los sistemas de archivos pueden registrar la creación y la hora del último acceso, y no todos los sistemas de archivos los registran de la misma manera. Por ejemplo, en el sistema de archivos FAT de Windows NT, la hora de creación tiene una resolución de 10 milisegundos, el tiempo de escritura tiene una resolución de 2 segundos y el tiempo de acceso tiene una resolución de 1 día (la fecha de acceso). En NTFS, el tiempo de acceso tiene una resolución de 1 hora. Además, FAT registra las horas en el disco en la hora local, pero NTFS registra las horas en el disco en formato UTC. Para obtener más información, vea [tiempos de archivo](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime. h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

El constructor.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) .

*nTime*<br/>
Fecha y hora expresadas como un valor de 64 bits.

### <a name="remarks"></a>Comentarios

El `CFileTime` objeto se puede crear con una fecha y una hora existentes desde `FILETIME` una estructura, o expresarse como un valor de 64 bits (en formatos de hora local o de hora universal coordinada (UTC)). El constructor predeterminado establece la hora en 0.

##  <a name="day"></a>  CFileTime::Day

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un día.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](#millisecond).

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

Llame a esta función estática para recuperar `CFileTime` un objeto que represente la fecha y hora actuales del sistema.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la fecha y hora actuales del sistema en formato de hora universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

Llame a este método para recuperar la hora del `CFileTime` objeto.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la fecha y la hora como un número de 64 bits, que puede estar en formato de hora universal coordinada (UTC) o local.

##  <a name="hour"></a>  CFileTime::Hour

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman una hora.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](#millisecond).

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

Llame a este método para convertir una hora de archivo local en una hora de archivo basándose en la hora universal coordinada (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTime` objeto que contiene la hora en formato UTC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>  CFileTime::Millisecond

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un milisegundo.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>CFileTime:: minute

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un minuto.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](#millisecond).

##  <a name="operator_-"></a>CFileTime:: Operator-

Este operador se usa para realizar la resta en un `CFileTime` objeto `CFileTimeSpan` o.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

*ft*<br/>
Objeto `CFileTime`.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTime` objeto o un `CFileTimeSpan` objeto que representa el resultado de la diferencia de tiempo entre los dos objetos.

##  <a name="operator_neq"></a>CFileTime:: Operator! =

Este operador compara dos `CFileTime` objetos para determinar si no son iguales.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar no es `CFileTime` igual al objeto; de lo contrario, es false.

##  <a name="operator_add"></a>CFileTime:: Operator +

Este operador se usa para sumar en un objeto `CFileTimeSpan`.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTime` objeto que representa el resultado de la hora original más una hora relativa.

##  <a name="operator_add_eq"></a>CFileTime:: Operator + =

Este operador se usa para sumar en un objeto `CFileTimeSpan` y asignar el resultado al objeto actual.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTime` actualizado, que representa el resultado de la hora original más una hora relativa.

##  <a name="operator_lt"></a>CFileTime:: Operator&lt;

Este operador compara dos objetos `CFileTime` para determinar el menor.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor (antes en el tiempo) que el segundo; de lo contrario, devuelve FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>CFileTime:: Operator&lt;=

Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el menor.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que (antes en el tiempo) o igual que el segundo; de lo contrario, es FALSE.

##  <a name="operator_eq"></a>CFileTime:: Operator =

Operador de asignación.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
`CFileTime` Objeto que contiene la nueva fecha y hora.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTime` actualizado.

##  <a name="operator_-_eq"></a>CFileTime:: Operator-=

Este operador se usa para realizar la resta en un `CFileTimeSpan` objeto y asignar el resultado al objeto actual.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
`CFileTimeSpan` Objeto que contiene el tiempo relativo que se va a restar.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTime` actualizado.

##  <a name="operator_eq_eq"></a>CFileTime:: Operator = =

Este operador compara dos objetos `CFileTime` para determinar si son iguales.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
`CFileTime` Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales; de lo contrario, es FALSE.

##  <a name="operator_gt"></a>CFileTime:: Operator&gt;

Este operador compara dos objetos `CFileTime` para determinar el mayor.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (más adelante en el tiempo) que el segundo; de lo contrario, es FALSE.

##  <a name="operator_gt_eq"></a>CFileTime:: Operator&gt;=

Este operador compara dos objetos `CFileTime` para determinar si son iguales o cuál es el mayor.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parámetros

*ft*<br/>
Objeto `CFileTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (más adelante en el tiempo) o igual que el segundo; de lo contrario, es FALSE.

##  <a name="second"></a>  CFileTime::Second

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman un día.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](#millisecond).

##  <a name="settime"></a>  CFileTime::SetTime

Llame a este método para establecer la fecha y la hora almacenadas por el `CFileTime` objeto.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parámetros

*nTime*<br/>
Valor de 64 bits que representa la fecha y la hora, en formato de hora universal coordinada (UTC) o local.

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

Llame a este método para convertir la hora basada en la hora universal coordinada (UTC) a la hora del archivo local.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTime` objeto que contiene la hora en formato de hora del archivo local.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

Un miembro de datos estático que almacena el número de intervalos de 100 nanosegundos que forman una semana.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](#millisecond).

## <a name="see-also"></a>Vea también

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan (clase)](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
