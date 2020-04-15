---
title: COleDateTimeSpan (clase)
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317740"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan (clase)

Representa un tiempo relativo, un intervalo de tiempo.

## <a name="syntax"></a>Sintaxis

```
class COleDateTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Construye un objeto `COleDateTimeSpan`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Genera una representación de `COleDateTimeSpan` cadena con formato de un objeto.|
|[COleDateTimeSpan::GetDays](#getdays)|Devuelve la parte del `COleDateTimeSpan` día del intervalo que representa este objeto.|
|[COleDateTimeSpan::GetHours](#gethours)|Devuelve la parte de `COleDateTimeSpan` hora del intervalo que representa este objeto.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Devuelve la parte de `COleDateTimeSpan` minutos del intervalo que representa este objeto.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Devuelve la segunda parte `COleDateTimeSpan` del intervalo que representa este objeto.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Obtiene el estado (validez) `COleDateTimeSpan` de este objeto.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Devuelve el número `COleDateTimeSpan` de días que representa este objeto.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Devuelve el número `COleDateTimeSpan` de horas que representa este objeto.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Devuelve el número `COleDateTimeSpan` de minutos que representa este objeto.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Devuelve el número `COleDateTimeSpan` de segundos que representa este objeto.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Establece el valor `COleDateTimeSpan` de este objeto.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Establece el status (validez) de este `COleDateTimeSpan` objeto.|

### <a name="public-operators"></a>Operadores públicos

|||
|-|-|
|[operador +, -](#operator_add_-)|Agregue, reste y `COleDateTimeSpan` cambie el signo de los valores.|
|[operador +, -](#operator_add_eq_-_eq)|Agregue y `COleDateTimeSpan` reste `COleDateTimeSpan` un valor de este valor.|
|[operador a la operadora de la red](#operator_eq)|Copia `COleDateTimeSpan` un valor.|
|[operador, <, <](#coledatetimespan_relational_operators)|Compare `COleDateTimeSpan` dos valores.|
|[operador double](#operator_double)|Convierte este `COleDateTimeSpan` valor en **double**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Contiene el **doble** subyacente `COleDateTimeSpan` para este objeto.|
|[COleDateTimeSpan::m_status](#m_status)|Contiene el estado `COleDateTimeSpan` de este objeto.|

## <a name="remarks"></a>Observaciones

`COleDateTimeSpan`no tiene una clase base.

A `COleDateTimeSpan` mantiene el tiempo en días.

`COleDateTimeSpan`se utiliza con su clase complementaria [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`encapsula el `DATE` tipo de datos de la automatización OLE. `COleDateTime`representa valores de tiempo absolutos. Todos `COleDateTime` los `COleDateTimeSpan` cálculos implican valores. La relación entre estas clases es análoga a la que hay entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Para obtener más `COleDateTime` `COleDateTimeSpan` información sobre las clases y, consulte el artículo [Fecha y hora: Compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan Operadores relacionales

Operadores de comparación.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parámetros

*dateSpan*<br/>
`COleDateTimeSpan` que se va comparar.

### <a name="return-value"></a>Valor devuelto

Estos operadores comparan dos valores de fecha y intervalo de tiempo y devuelven TRUE si la condición es true; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Se producirá un ATLASSERT si cualquiera de los operandos no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan

Construye un objeto `COleDateTimeSpan`.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parámetros

*dblSpanSrc*<br/>
El número de días que se `COleDateTimeSpan` van a copiar en el nuevo objeto.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indique los valores de día y hora `COleDateTimeSpan` que se van a copiar en el nuevo objeto.

### <a name="remarks"></a>Observaciones

Todos estos constructores `COleDateTimeSpan` crean nuevos objetos inicializados en el valor especificado. A continuación se ofrece una breve descripción de cada uno de estos constructores:

- **COleDateTimeSpan( )** Construye un `COleDateTimeSpan` objeto inicializado en 0.

- **COleDateTimeSpan(** `dblSpanSrc` **)** Construye un `COleDateTimeSpan` objeto a partir de un valor de punto flotante.

- **COleDateTimeSpan(** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** Construye un `COleDateTimeSpan` objeto inicializado en los valores numéricos especificados.

El estado del `COleDateTimeSpan` nuevo objeto se establece en válido.

Para obtener más información `COleDateTimeSpan` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Format

Genera una representación de `COleDateTimeSpan` cadena con formato de un objeto.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*pFormat*<br/>
Cadena de formato `printf` similar a la cadena de formato. Los códigos de formato,`%`precedidos por un `COleDateTimeSpan` signo de porcentaje ( ), se reemplazan por el componente correspondiente. Otros caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. El valor y el significado `Format` de los códigos de formato para se enumeran a continuación:

- **%H** Horas en el día actual

- **%M** Minutos en la hora actual

- **%S** Segundos en el minuto actual

- **%%** Signo porcentual

Los cuatro códigos de formato enumerados anteriormente son los únicos códigos que Format aceptará.

-

*nID*<br/>
El identificador de recurso para la cadena de control de formato.

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene el valor de fecha y intervalo de tiempo con formato.

### <a name="remarks"></a>Observaciones

Llame a estas funciones para crear una representación con formato del valor de intervalo de tiempo. Si el estado `COleDateTimeSpan` de este objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena de retorno se especifica mediante el recurso de cadena IDS_INVALID_DATETIMESPAN.

A continuación se presenta una breve descripción de los formularios para esta función:

**Format(** *pFormat* **)**<br/>
Este formulario da formato al valor mediante la cadena de formato que contiene `printf`códigos de formato especiales precedidos por un signo de porcentaje (%), como en . La cadena de formato se pasa como parámetro a la función.

**Formato(** *nID* **)**<br/>
Este formulario da formato al valor mediante la cadena de formato que contiene `printf`códigos de formato especiales precedidos por un signo de porcentaje (%), como en . La cadena de formato es un recurso. El identificador de este recurso de cadena se pasa como parámetro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

Recupera la parte del día de este valor de fecha y intervalo de tiempo.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Valor devuelto

La parte del día de este valor de fecha y intervalo de tiempo.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre aproximadamente - 3.615.000 y 3.615.000.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan::GetHours

Recupera la parte de hora de este valor de fecha y intervalo de tiempo.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

La parte de horas de este valor de fecha y intervalo de tiempo.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre - 23 y 23.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan::GetMinutes

Recupera la parte de minutos de este valor de fecha y intervalo de tiempo.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

La parte de minutos de este valor de fecha y intervalo de tiempo.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre - 59 y 59.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds

Recupera la segunda parte de este valor de fecha y intervalo de tiempo.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

La parte de segundos de este valor de fecha/intervalo de tiempo.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre - 59 y 59.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus

Obtiene el estado (validez) `COleDateTimeSpan` de este objeto.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valor devuelto

El estado `COleDateTimeSpan` de este valor.

### <a name="remarks"></a>Observaciones

El valor devuelto se `DateTimeSpanStatus` define mediante el tipo `COleDateTimeSpan` enumerado, que se define dentro de la clase.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleDateTimeSpan::valid`Indica que `COleDateTimeSpan` este objeto es válido.

- `COleDateTimeSpan::invalid`Indica que `COleDateTimeSpan` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTimeSpan::null`Indica que `COleDateTimeSpan` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

El estado `COleDateTimeSpan` de un objeto no es válido en los siguientes casos:

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante `+=` `-=`una operación de asignación aritmética, es decir, o .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se `SetStatus`estableció explícitamente en no válido mediante .

Para obtener más información acerca de las operaciones que pueden establecer el estado en no válido, vea [COleDateTimeSpan::operator + , -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +-, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Para obtener más información `COleDateTimeSpan` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Recupera este valor de fecha y intervalo de tiempo expresado en días.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Valor devuelto

Este valor de fecha y intervalo de tiempo expresado en días. Aunque esta función es prototipo para devolver un double, siempre devolverá un valor entero.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre aproximadamente - 3.65e6 y 3.65e6.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

Recupera este valor de fecha y intervalo de tiempo expresado en horas.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

Este valor de fecha y intervalo de tiempo expresado en horas. Aunque esta función es prototipo para devolver un double, siempre devolverá un valor entero.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre aproximadamente - 8.77e7 y 8.77e7.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

Recupera este valor de fecha y intervalo de tiempo expresado en minutos.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

Este valor de fecha y intervalo de tiempo expresado en minutos. Aunque esta función es prototipo para devolver un double, siempre devolverá un valor entero.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre aproximadamente - 5.26e9 y 5.26e9.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

Recupera este valor de fecha y intervalo de tiempo expresado en segundos.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

Este valor de fecha/intervalo de tiempo expresado en segundos. Aunque esta función es prototipo para devolver un double, siempre devolverá un valor entero.

### <a name="remarks"></a>Observaciones

Los valores devueltos de esta función oscilan entre aproximadamente - 3.16e11 a 3.16e11.

Para otras funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan::m_span

El valor **double** subyacente `COleDateTime` para este objeto.

```
double m_span;
```

### <a name="remarks"></a>Observaciones

Este valor expresa la fecha/intervalo de tiempo en días.

> [!CAUTION]
> Cambiar el valor **double** en el miembro de `COleDateTimeSpan` datos double cambiará el valor de este objeto. No cambia el estado `COleDateTimeSpan` de este objeto.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan::m_status

El tipo de este miembro de `DateTimeSpanStatus`datos es el `COleDateTimeSpan` tipo enumerado, que se define dentro de la clase.

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Observaciones

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleDateTimeSpan::valid`Indica que `COleDateTimeSpan` este objeto es válido.

- `COleDateTimeSpan::invalid`Indica que `COleDateTimeSpan` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTimeSpan::null`Indica que `COleDateTimeSpan` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

El estado `COleDateTimeSpan` de un objeto no es válido en los siguientes casos:

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante `+=` `-=`una operación de asignación aritmética, es decir, o .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información acerca de las operaciones que pueden establecer el estado en no válido, vea [COleDateTimeSpan::operator + , -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) y [COleDateTimeSpan::operator +-, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para obtener más precauciones con respecto a la configuración explícita de este miembro de datos.

Para obtener más información `COleDateTimeSpan` acerca de los límites de los valores, consulte el artículo [Fecha y hora: compatibilidad con automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::operator ?

Copia `COleDateTimeSpan` un valor.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Observaciones

Este operador de asignación sobrecargado copia el `COleDateTimeSpan` valor de fecha y intervalo de tiempo de origen en este objeto.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::operador +, -

Agregue, reste y `COleDateTimeSpan` cambie el signo de los valores.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Observaciones

Los dos primeros operadores le permiten agregar y restar valores de fecha y intervalo de tiempo. El tercero le permite cambiar el signo de un valor de fecha y intervalo de tiempo.

Si cualquiera de los operandos es null, el estado del valor resultante `COleDateTimeSpan` es null.

Si cualquiera de los operandos no es válido y el `COleDateTimeSpan` otro no es null, el estado del valor resultante no es válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operador +-, --

Agregue y `COleDateTimeSpan` reste `COleDateTimeSpan` un valor de este valor.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Observaciones

Estos operadores permiten agregar y restar valores `COleDateTimeSpan` de fecha y intervalo de tiempo de este objeto. Si cualquiera de los operandos es null, el estado del valor resultante `COleDateTimeSpan` es null.

Si cualquiera de los operandos no es válido y el `COleDateTimeSpan` otro no es null, el estado del valor resultante no es válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::operator double

Convierte este `COleDateTimeSpan` valor en **double**.

```
operator double() const throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve el `COleDateTimeSpan` valor de este valor como un número de punto flotante de días.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan

Establece el valor de este valor de fecha y intervalo de tiempo.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parámetros

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indique los valores de intervalo de fecha y `COleDateTimeSpan` intervalo de tiempo que se van a copiar en este objeto.

### <a name="remarks"></a>Observaciones

Para las funciones que `COleDateTimeSpan` consultan el valor de un objeto, consulte las siguientes funciones miembro:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan::SetStatus

Establece el status (validez) de este `COleDateTimeSpan` objeto.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El nuevo valor `COleDateTimeSpan` de estado para este objeto.

### <a name="remarks"></a>Observaciones

El *Status* valor del parámetro `DateTimeSpanStatus` Status se define mediante el `COleDateTimeSpan` tipo enumerado, que se define dentro de la clase.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleDateTimeSpan::valid`Indica que `COleDateTimeSpan` este objeto es válido.

- `COleDateTimeSpan::invalid`Indica que `COleDateTimeSpan` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTimeSpan::null`Indica que `COleDateTimeSpan` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

   > [!CAUTION]
   > Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se usará más a menudo para establecer el estado en **null** o **invalid .** Tenga en cuenta que el operador de asignación ([operator )](#operator_eq)y [SetDateTimeSpan](#setdatetimespan) establecen el estado del objeto en función de los valores de origen.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Consulte también

[Clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[Clase CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Clase CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
