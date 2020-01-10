---
title: CFileTimeSpan (Clase)
ms.date: 01/06/2020
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
ms.openlocfilehash: 9220ed8373e78db727b43ecb59880dcfbcc98f96
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755052"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan (Clase)

Esta clase proporciona métodos para administrar valores de fecha y hora relativos asociados a un archivo.

## <a name="syntax"></a>Sintaxis

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Llame a este método para recuperar el intervalo de tiempo del objeto `CFileTimeSpan`.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Llame a este método para establecer el intervalo de tiempo del objeto `CFileTimeSpan`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Realiza una resta en un objeto de `CFileTimeSpan`.|
|[CFileTimeSpan::operator !=](#operator_neq)|Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.|
|[CFileTimeSpan::operator +](#operator_add)|Realiza sumas en un objeto de `CFileTimeSpan`.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Realiza sumas en un objeto de `CFileTimeSpan` y asigna el resultado al objeto actual.|
|[CFileTimeSpan:: Operator &lt;](#operator_lt)|Compara dos objetos `CFileTimeSpan` para determinar el menor.|
|[CFileTimeSpan:: Operator &lt;=](#operator_lt_eq)|Compara dos objetos `CFileTimeSpan` para determinar la igualdad o el menor.|
|[CFileTimeSpan::operator =](#operator_eq)|Operador de asignación.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Realiza una resta en un objeto de `CFileTimeSpan` y asigna el resultado al objeto actual.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compara dos objetos `CFileTimeSpan` para determinar si son iguales.|
|[CFileTimeSpan:: Operator &gt;](#operator_gt)|Compara dos objetos `CFileTimeSpan` para determinar el mayor.|
|[CFileTimeSpan:: Operator &gt;=](#operator_gt_eq)|Compara dos objetos `CFileTimeSpan` para determinar la igualdad o el mayor.|

## <a name="remarks"></a>Notas

Esta clase proporciona métodos para controlar los períodos de tiempo relativos en las unidades que el sistema de archivos utiliza. Estas unidades se usan a menudo en operaciones relacionadas con la creación, el último acceso o la última modificación de un archivo. Los métodos de esta clase se usan con frecuencia junto con los objetos de la [clase CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Requisitos de

**Encabezado:** atltime. h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

El constructor.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan` existente.

\ *nSpan*
Un período de tiempo en milisegundos.

### <a name="remarks"></a>Notas

El objeto de `CFileTimeSpan` se puede crear con un objeto `CFileTimeSpan` existente, o expresarse como un valor de 64 bits. El constructor predeterminado establece el intervalo de tiempo en 0.

## <a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Llame a este método para recuperar el intervalo de tiempo del objeto `CFileTimeSpan`.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el intervalo de tiempo en milisegundos.

## <a name="operator_-"></a>  CFileTimeSpan::operator -

Realiza una resta en un objeto de `CFileTimeSpan`.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto `CFileTimeSpan` que representa el resultado de la diferencia entre dos intervalos de tiempo.

## <a name="operator_neq"></a>  CFileTimeSpan::operator !=

Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se está comparando no es igual al objeto `CFileTimeSpan`; en caso contrario, FALSE.

## <a name="operator_add"></a>  CFileTimeSpan::operator +

Realiza sumas en un objeto de `CFileTimeSpan`.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto `CFileTimeSpan` que contiene la suma de los dos intervalos de tiempo.

## <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Realiza sumas en un objeto `CFileTimeSpan` y asigna el resultado al objeto actual.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado que contiene la suma de los dos intervalos de tiempo.

## <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Compara dos objetos `CFileTimeSpan` para determinar el menor.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor (es decir, representa un período de tiempo más corto) que el segundo; de lo contrario, es FALSE.

## <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Compara dos objetos `CFileTimeSpan` para determinar la igualdad o el menor.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que (es decir, representa un período de tiempo más corto) o igual que el segundo; de lo contrario, es FALSE.

## <a name="operator_eq"></a>  CFileTimeSpan::operator =

Operador de asignación.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado.

## <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

Realiza una resta en un objeto de `CFileTimeSpan` y asigna el resultado al objeto actual.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Un objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado.

## <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Compara dos objetos `CFileTimeSpan` para determinar si son iguales.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales; de lo contrario, es FALSE.

## <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Compara dos objetos `CFileTimeSpan` para determinar el mayor.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) que el segundo; de lo contrario, es FALSE.

## <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Compara dos objetos `CFileTimeSpan` para determinar la igualdad o el mayor.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

\ de *intervalo*
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) o igual que el segundo; de lo contrario, es FALSE.

## <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Llame a este método para establecer el intervalo de tiempo del objeto `CFileTimeSpan`.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameters

\ *nSpan*
Nuevo valor para el intervalo de tiempo en unidades de 100-nanosegundos. Para obtener más información, vea [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Vea también

\ [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)
\ de la [clase CFileTime](cfiletime-class.md)
\ [gráfico de jerarquía](../../mfc/hierarchy-chart.md)
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
