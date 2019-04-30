---
title: CTimeSpan (clase)
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
ms.openlocfilehash: 3c80260c1f57e49a34b4e9f3331f4d0d69ab30ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252538"
---
# <a name="ctimespan-class"></a>CTimeSpan (clase)

Un período de tiempo, que se almacena internamente como el número de segundos en el intervalo de tiempo.

## <a name="syntax"></a>Sintaxis

```
class CTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Construye `CTimeSpan` objetos de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Convierte un `CTimeSpan` en una cadena con formato.|
|[CTimeSpan::GetDays](#getdays)|Devuelve un valor que representa el número de días completos en este `CTimeSpan`.|
|[CTimeSpan::GetHours](#gethours)|Devuelve un valor que representa el número de horas del día actual (-23 y 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Devuelve un valor que representa el número de minutos durante la hora actual (de-59 a 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Devuelve un valor que representa el número de segundos del minuto actual (de-59 a 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Devuelve el valor de la `CTimeSpan` objeto.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Devuelve un valor que representa el número total de horas completas de este `CTimeSpan`.|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Devuelve un valor que representa el número total de minutos completadas en este `CTimeSpan`.|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Devuelve un valor que representa el número total de segundos completadas en este `CTimeSpan`.|
|[CTimeSpan::Serialize64](#serialize64)|Serializa los datos hacia o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator + -](#operator_add_-)|Agrega y resta `CTimeSpan` objetos.|
|[operator += -=](#operator_add_eq_-_eq)|Se agrega y se resta un `CTimeSpan` objetos hacia y desde este `CTimeSpan`.|
|[operador == < etcetera.](#ctimespan_comparison_operators)|Compara dos valores de tiempo relativo.|

## <a name="remarks"></a>Comentarios

`CTimeSpan` no tiene una clase base.

`CTimeSpan` funciones convierten segundos en diversas combinaciones de días, horas, minutos y segundos.

El `CTimeSpan` objeto está almacenado en un **__time64_t** estructura, que es de 8 bytes.

Una clase complementaria, [CTime](../../atl-mfc-shared/reference/ctime-class.md), representa un tiempo absoluto.

El `CTime` y `CTimeSpan` clases no están diseñadas para la derivación. Dado que no hay ninguna función virtual, el tamaño de ambos `CTime` y `CTimeSpan` objetos es exactamente de 8 bytes. La mayoría de las funciones de miembro están alineados.

Para obtener más información sobre el uso de `CTimeSpan`, consulte los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [administración del tiempo](../../c-runtime-library/time-management.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

##  <a name="ctimespan_comparison_operators"></a>  Operadores de comparación CTimeSpan

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

*span*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Estos operadores comparan dos valores de tiempo relativo. Devuelven TRUE si la condición es true; en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan

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
Un `CTimeSpan` objeto que ya existe.

*time*<br/>
Un **__time64_t** valor de tiempo, que es el número de segundos en el intervalo de tiempo.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Días, horas, minutos y segundos, respectivamente.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean un nuevo `CTimeSpan` objeto inicializado con el tiempo relativo especificado. Cada constructor se describe a continuación:

- `CTimeSpan( );` Construye un sin inicializar `CTimeSpan` objeto.

- `CTimeSpan( const CTimeSpan& );` Construye un `CTimeSpan` objeto desde otro `CTimeSpan` valor.

- `CTimeSpan( __time64_t );` Construye un `CTimeSpan` objeto desde un **__time64_t** tipo.

- `CTimeSpan( LONG, int, int, int );` Construye un `CTimeSpan` objeto a partir de los componentes con cada componente se limita a los siguientes intervalos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*lDays*|0-25.000 (aproximadamente)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Tenga en cuenta que la versión de depuración de la biblioteca Microsoft Foundation Class afirma si uno o varios de los componentes de hora día está fuera del intervalo. Es su responsabilidad para validar los argumentos antes de llamar a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

##  <a name="format"></a>  CTimeSpan::Format

Genera una cadena con formato que corresponde a este `CTimeSpan`.

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*pFormat*, *pszFormat*<br/>
Cadena de un formato similar a la `printf` cadena de formato. Códigos de formato, precedidos por un porcentaje (`%`) inicie sesión, se reemplazan por la correspondiente `CTimeSpan` componente. Otros caracteres en la cadena de formato se copian sin cambios a la cadena devuelta. El valor y el significado de los códigos de formato para `Format` se enumeran a continuación:

- **%D** total de días en este `CTimeSpan`

- **%H** horas del día actual

- **%M** minutos durante la hora actual

- **%S** segundos del minuto actual

- **%%** Signo de porcentaje

*nID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene la hora con formato.

### <a name="remarks"></a>Comentarios

La versión de la biblioteca de depuración comprueba los códigos de formato y valida si el código no está en la lista anterior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

##  <a name="getdays"></a>  CTimeSpan::GetDays

Devuelve un valor que representa el número de días completos en este `CTimeSpan`.

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de días completos de 24 horas en el intervalo de tiempo. Este valor puede ser negativo si el intervalo de tiempo es negativo.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que puede hacer que el horario de verano `GetDays` para devolver un resultado sorprendente potencialmente. Por ejemplo, al horario de verano está vigente, `GetDays` informa del número de días entre el 1 de abril y el 1 de mayo como 29, 30 no, porque se ha reducido por una hora de un día de abril y, por tanto, no se considera un día completo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

##  <a name="gethours"></a>  CTimeSpan::GetHours

Devuelve un valor que representa el número de horas del día actual (-23 y 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de horas del día actual. El intervalo es -23 y 23.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

##  <a name="getminutes"></a>  CTimeSpan::GetMinutes

Devuelve un valor que representa el número de minutos durante la hora actual (de-59 a 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de minutos de la hora actual. El intervalo es de-59 a 59.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHours](#gethours).

##  <a name="getseconds"></a>  CTimeSpan::GetSeconds

Devuelve un valor que representa el número de segundos del minuto actual (de-59 a 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de segundos del minuto actual. El intervalo es de-59 a 59.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHours](#gethours).

##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan

Devuelve el valor de la `CTimeSpan` objeto.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor actual de la `CTimeSpan` objeto.

##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours

Devuelve un valor que representa el número total de horas completas de este `CTimeSpan`.

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de horas completas de este `CTimeSpan`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes

Devuelve un valor que representa el número total de minutos completadas en este `CTimeSpan`.

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de minutos completadas en este `CTimeSpan`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalHours](#gettotalhours).

##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds

Devuelve un valor que representa el número total de segundos completadas en este `CTimeSpan`.

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número total de segundos completadas en este `CTimeSpan`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetTotalHours](#gettotalhours).

##  <a name="operator_add_-"></a>  CTimeSpan::operator +, -

Agrega y resta `CTimeSpan` objetos.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*span*<br/>
Valor que se agrega a la `CTimeSpan` objeto.

### <a name="return-value"></a>Valor devuelto

Un `CTimeSpan` objeto que representa el resultado de la operación.

### <a name="remarks"></a>Comentarios

Estos dos operadores permiten sumar y restar `CTimeSpan` objetos a y desde ellos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator +=, -=

Se agrega y se resta un `CTimeSpan` objetos hacia y desde este `CTimeSpan`.

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*span*<br/>
Valor que se agrega a la `CTimeSpan` objeto.

### <a name="return-value"></a>Valor devuelto

La actualización `CTimeSpan` objeto.

### <a name="remarks"></a>Comentarios

Estos operadores permiten sumar y restar un `CTimeSpan` objetos hacia y desde este `CTimeSpan`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

##  <a name="serialize64"></a>  CTimeSpan::Serialize64

> [!NOTE]
>  Este método solo está disponible en proyectos de MFC.

Serializa los datos asociados con la variable de miembro a o desde un archivo.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
La `CArchive` objeto que se va a actualizar.

### <a name="return-value"></a>Valor devuelto

La actualización `CArchive` objeto.

## <a name="see-also"></a>Vea también

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
