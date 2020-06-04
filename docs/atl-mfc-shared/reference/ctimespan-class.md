---
title: Clase CTimeSpan
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317499"
---
# <a name="ctimespan-class"></a>Clase CTimeSpan

Una cantidad de tiempo, que se almacena internamente como el número de segundos en el intervalo de tiempo.

## <a name="syntax"></a>Sintaxis

```
class CTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Construye `CTimeSpan` objetos de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTimeSpan::Formato](#format)|Convierte a `CTimeSpan` en una cadena con formato.|
|[CTimeSpan::GetDays](#getdays)|Devuelve un valor que representa el número `CTimeSpan`de días completos en este archivo .|
|[CTimeSpan::GetHours](#gethours)|Devuelve un valor que representa el número de horas del día actual (-23 a 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Devuelve un valor que representa el número de minutos de la hora actual (-59 a 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Devuelve un valor que representa el número de segundos del minuto actual (-59 a 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Devuelve el valor `CTimeSpan` del objeto.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Devuelve un valor que representa el número `CTimeSpan`total de horas completas en este archivo .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Devuelve un valor que representa el número `CTimeSpan`total de minutos completos en este archivo .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Devuelve un valor que representa el número `CTimeSpan`total de segundos completos en este archivo .|
|[CTimeSpan::Serialize64](#serialize64)|Serializa los datos hacia o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador + -](#operator_add_-)|Agrega y resta objetos. `CTimeSpan`|
|[operador +- -](#operator_add_eq_-_eq)|Agrega y resta `CTimeSpan` un objeto `CTimeSpan`a y desde este archivo .|
|[operador <, etc.](#ctimespan_comparison_operators)|Compara dos valores de tiempo relativos.|

## <a name="remarks"></a>Observaciones

`CTimeSpan`no tiene una clase base.

`CTimeSpan`las funciones convierten los segundos en varias combinaciones de días, horas, minutos y segundos.

El `CTimeSpan` objeto se almacena en una estructura **__time64_t,** que es de 8 bytes.

Una clase complementaria, [CTime](../../atl-mfc-shared/reference/ctime-class.md), representa un tiempo absoluto.

Las `CTime` `CTimeSpan` clases y no están diseñadas para la derivación. Dado que no hay funciones `CTime` virtuales, el tamaño de ambos y `CTimeSpan` objetos es exactamente 8 bytes. La mayoría de las funciones miembro están en línea.

Para obtener más `CTimeSpan`información sobre el uso , consulte los artículos [Fecha y hora](../../atl-mfc-shared/date-and-time.md)y [Administración](../../c-runtime-library/time-management.md) de tiempo según la Referencia de la biblioteca en tiempo *de ejecución*.

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>Operadores de comparación de CTimeSpan

Operadores de comparación.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Estos operadores comparan dos valores de tiempo relativos. Devuelven TRUE si la condición es true; de lo contrario FALSO.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan::CTimeSpan

Construye `CTimeSpan` objetos de varias maneras.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>Parámetros

*timeSpanSrc*<br/>
Objeto `CTimeSpan` que ya existe.

*time*<br/>
Un valor de tiempo **__time64_t,** que es el número de segundos en el intervalo de tiempo.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Días, horas, minutos y segundos, respectivamente.

### <a name="remarks"></a>Observaciones

Todos estos constructores `CTimeSpan` crean un nuevo objeto inicializado con el tiempo relativo especificado. Cada constructor se describe a continuación:

- `CTimeSpan( );`Construye un objeto `CTimeSpan` no inicializado.

- `CTimeSpan( const CTimeSpan& );`Construye un `CTimeSpan` objeto `CTimeSpan` a partir de otro valor.

- `CTimeSpan( __time64_t );`Construye un `CTimeSpan` objeto a partir de un tipo **de __time64_t.**

- `CTimeSpan( LONG, int, int, int );`Construye un `CTimeSpan` objeto a partir de componentes con cada componente restringido a los siguientes rangos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*lDays*|0-25.000 (aproximadamente)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Tenga en cuenta que la versión de depuración de la biblioteca de clases de Microsoft Foundation afirma si uno o varios de los componentes del día de tiempo está fuera del intervalo. Es su responsabilidad validar los argumentos antes de llamar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan::Formato

Genera una cadena con formato `CTimeSpan`que corresponde a esto .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*pFormat*, *pszFormat*<br/>
Cadena de formato `printf` similar a la cadena de formato. Los códigos de formato,`%`precedidos por un `CTimeSpan` signo de porcentaje ( ), se reemplazan por el componente correspondiente. Otros caracteres de la cadena de formato se copian sin cambios en la cadena devuelta. El valor y el significado `Format` de los códigos de formato para se enumeran a continuación:

- **%D** Días totales en este`CTimeSpan`

- **%H** Horas en el día actual

- **%M** Minutos en la hora actual

- **%S** Segundos en el minuto actual

- **%%** Signo porcentual

*nID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene la hora con formato.

### <a name="remarks"></a>Observaciones

La versión de depuración de la biblioteca comprueba los códigos de formato y afirma si el código no está en la lista anterior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan::GetDays

Devuelve un valor que representa el número `CTimeSpan`de días completos en este archivo .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de días completos de 24 horas en el intervalo de tiempo. Este valor puede ser negativo si el intervalo de tiempo es negativo.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `GetDays` el horario de verano puede hacer que devuelva un resultado potencialmente sorprendente. Por ejemplo, cuando el DST está en vigor, `GetDays` informa del número de días entre el 1 de abril y el 1 de mayo como 29, no 30, porque un día de abril se acorta una hora y, por lo tanto, no cuenta como un día completo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan::GetHours

Devuelve un valor que representa el número de horas del día actual (-23 a 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de horas del día actual. El rango es de -23 a 23.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan::GetMinutes

Devuelve un valor que representa el número de minutos de la hora actual (-59 a 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de minutos de la hora actual. El rango es de -59 a 59.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan::GetSeconds

Devuelve un valor que representa el número de segundos del minuto actual (-59 a 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de segundos en el minuto actual. El rango es de -59 a 59.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan::GetTimeSpan

Devuelve el valor `CTimeSpan` del objeto.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor `CTimeSpan` actual del objeto.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan::GetTotalHours

Devuelve un valor que representa el número `CTimeSpan`total de horas completas en este archivo .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de `CTimeSpan`horas completas en este archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan::GetTotalMinutes

Devuelve un valor que representa el número `CTimeSpan`total de minutos completos en este archivo .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de `CTimeSpan`minutos completos en este archivo .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan::GetTotalSeconds

Devuelve un valor que representa el número `CTimeSpan`total de segundos completos en este archivo .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de `CTimeSpan`segundos completos en este archivo .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::operador +, -

Agrega y resta objetos. `CTimeSpan`

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
El valor que `CTimeSpan` se va a agregar al objeto.

### <a name="return-value"></a>Valor devuelto

Objeto `CTimeSpan` que representa el resultado de la operación.

### <a name="remarks"></a>Observaciones

Estos dos operadores le `CTimeSpan` permiten agregar y restar objetos entre sí.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan::operador +-, --

Agrega y resta `CTimeSpan` un objeto `CTimeSpan`a y desde este archivo .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*<br/>
El valor que `CTimeSpan` se va a agregar al objeto.

### <a name="return-value"></a>Valor devuelto

El `CTimeSpan` objeto actualizado.

### <a name="remarks"></a>Observaciones

Estos operadores le permiten `CTimeSpan` agregar y restar un objeto a y desde este `CTimeSpan`archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan::Serialize64

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

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
