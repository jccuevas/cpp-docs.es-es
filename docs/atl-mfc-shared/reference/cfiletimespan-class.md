---
title: CFileTimeSpan (Clase)
description: La clase CFileTimeSpan de Active Template Library (ATL) y Microsoft Foundation Classes (MFC) administra los intervalos de tiempo en unidades FILETIME.
ms.date: 01/10/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317853"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan (Clase)

Esta clase proporciona métodos para administrar los valores de fecha y hora relativos asociados a un archivo.

## <a name="syntax"></a>Sintaxis

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Llame a este método para `CFileTimeSpan` recuperar el intervalo de tiempo del objeto.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Llame a este método para `CFileTimeSpan` establecer el intervalo de tiempo del objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileTimeSpan::operador -](#operator_-)|Realiza restas en `CFileTimeSpan` un objeto.|
|[CFileTimeSpan::operator !o](#operator_neq)|Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.|
|[CFileTimeSpan::operador +](#operator_add)|Realiza la adición en un `CFileTimeSpan` objeto.|
|[CFileTimeSpan::operador +o](#operator_add_eq)|Realiza la adición en un `CFileTimeSpan` objeto y asigna el resultado al objeto actual.|
|[CFileTimeSpan::operator&lt;](#operator_lt)|Compara dos `CFileTimeSpan` objetos para determinar el menor.|
|[CFileTimeSpan::operator&lt;=](#operator_lt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el menor.|
|[CFileTimeSpan::operator ?](#operator_eq)|El operador de asignación.|
|[CFileTimeSpan::operador --](#operator_-_eq)|Realiza la resta `CFileTimeSpan` en un objeto y asigna el resultado al objeto actual.|
|[CFileTimeSpan::operador ?](#operator_eq_eq)|Compara dos objetos `CFileTimeSpan` para determinar si son iguales.|
|[CFileTimeSpan::operator&gt;](#operator_gt)|Compara dos `CFileTimeSpan` objetos para determinar el más grande.|
|[CFileTimeSpan::operator&gt;=](#operator_gt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el más grande.|

## <a name="remarks"></a>Observaciones

La `CFileTimeSpan` clase proporciona métodos para controlar períodos de tiempo relativos en las unidades que utiliza el sistema de archivos. Estas unidades se utilizan a menudo en operaciones de archivo, como cuando se creó un archivo, se accedió por última vez o se modificó por última vez. Los métodos de esta clase se utilizan con frecuencia junto con [CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) objetos de clase.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

El constructor.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` existente.

*nSpan*\
Un período de tiempo en unidades FILETIME.

### <a name="remarks"></a>Observaciones

El `CFileTimeSpan` objeto se puede `CFileTimeSpan` crear utilizando un objeto existente o expresarse como un valor de 64 bits en unidades FILETIME de 100 nanosegundos. Para obtener más información, vea [CFileTime](cfiletime-class.md). El constructor predeterminado establece el intervalo de tiempo en 0.

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Llame a este método para `CFileTimeSpan` recuperar el intervalo de tiempo del objeto.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el intervalo de tiempo en unidades FILETIME de 100 nanosegundos. Para obtener más información, vea [CFileTime](cfiletime-class.md).

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::operador -

Realiza restas en `CFileTimeSpan` un objeto.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTimeSpan` un objeto que representa el resultado de la diferencia entre dos intervalos de tiempo.

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::operator !o

Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se `CFileTimeSpan` compara no es igual al objeto; de lo contrario FALSO.

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::operador +

Realiza la adición en un `CFileTimeSpan` objeto.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve `CFileTimeSpan` un objeto que contiene la suma de los dos intervalos de tiempo.

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::operador +o

Realiza la adición en un `CFileTimeSpan` objeto y asigna el resultado al objeto actual.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTimeSpan` objeto actualizado que contiene la suma de los dos intervalos de tiempo.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::operator&lt;

Compara dos `CFileTimeSpan` objetos para determinar el menor.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor (es decir, representa un período de tiempo más corto) que el segundo, de lo contrario FALSE.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::operator&lt;=

Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el menor.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que (es decir, representa un período de tiempo más corto) o igual que el segundo, de lo contrario FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::operator ?

El operador de asignación.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTimeSpan` objeto actualizado.

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::operador --

Realiza la resta `CFileTimeSpan` en un objeto y asigna el resultado al objeto actual.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` .

### <a name="return-value"></a>Valor devuelto

Devuelve el `CFileTimeSpan` objeto actualizado.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::operador ?

Compara dos objetos `CFileTimeSpan` para determinar si son iguales.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales, de lo contrario FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::operator&gt;

Compara dos `CFileTimeSpan` objetos para determinar el más grande.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) que el segundo, de lo contrario FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::operator&gt;=

Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el más grande.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*envergadura*\
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) o igual que el segundo, de lo contrario FALSE.

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Llame a este método para `CFileTimeSpan` establecer el intervalo de tiempo del objeto.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parámetros

*nSpan*\
El nuevo valor para el intervalo de tiempo en unidades FILETIME de 100 nanosegundos. Para obtener más información, vea [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Consulte también

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[Clase CFileTime](cfiletime-class.md)\
[Gráfico de jerarquía](../../mfc/hierarchy-chart.md)\
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
