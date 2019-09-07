---
title: Clase CComSafeArrayBound
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 0386092ac26e71fcf5e840594a6b07f56cc9badd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739748"
---
# <a name="ccomsafearraybound-class"></a>Clase CComSafeArrayBound

Esta clase es un contenedor para una estructura [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) .

## <a name="syntax"></a>Sintaxis

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|El constructor.|
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos.|
|[GetLowerBound](#getlowerbound)|Llame a este método para devolver el límite inferior.|
|[GetUpperBound](#getupperbound)|Llame a este método para devolver el límite superior.|
|[SetCount](#setcount)|Llame a este método para establecer el número de elementos.|
|[SetLowerBound](#setlowerbound)|Llame a este método para establecer el límite inferior.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Establece el `CComSafeArrayBound` en un nuevo valor.|

## <a name="remarks"></a>Comentarios

Esta clase es un contenedor para la `SAFEARRAYBOUND` estructura utilizada por [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Proporciona métodos para consultar y establecer los límites superior e inferior de una sola dimensión de un `CComSafeArray` objeto y el número de elementos que contiene. Un `CComSafeArray` objeto multidimensional utiliza una matriz de `CComSafeArrayBound` objetos, uno para cada dimensión. Por consiguiente, al utilizar métodos como [getCount](#getcount), tenga en cuenta que este método no devolverá el número total de elementos de una matriz multidimensional.

**Encabezado:** atlsafe.h

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

El constructor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos de la matriz.

*lLowerBound*<br/>
Límite inferior desde el que se numera la matriz.

### <a name="remarks"></a>Comentarios

Si se va a tener acceso a la matriz desde C++ un programa, se recomienda definir el límite inferior como 0. Puede ser preferible usar un valor de límite inferior diferente si la matriz se va a usar con otros lenguajes, como Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Llame a este método para devolver el número de elementos.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos.

### <a name="remarks"></a>Comentarios

Si el objeto `CComSafeArray` asociado representa una matriz multidimensional, este método solo devolverá el número total de elementos de la dimensión situada más a la derecha. Use [CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) para obtener el número total de elementos.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Llame a este método para devolver el límite inferior.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior del `CComSafeArrayBound` objeto.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Llame a este método para devolver el límite superior.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior del `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

El límite superior depende del número de elementos y del valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente en 9.

##  <a name="operator_eq"></a>CComSafeArrayBound:: Operator =

Establece el `CComSafeArrayBound` en un nuevo valor.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*enlaza*<br/>
Objeto `CComSafeArrayBound`.

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

El `CComSafeArrayBound` objeto se puede asignar mediante una existente `CComSafeArrayBound`o proporcionando el número de elementos, en cuyo caso el límite inferior se establece en 0 de forma predeterminada.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Llame a este método para establecer el número de elementos.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos `CComSafeArrayBound` del objeto.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Llame a este método para establecer el límite inferior.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parámetros

*lLowerBound*<br/>
Límite inferior.

### <a name="return-value"></a>Valor devuelto

Devuelve el nuevo límite inferior del `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

Si se va a tener acceso a la matriz desde un C++ programa visual, se recomienda definir el límite inferior como 0. Puede ser preferible usar un valor de límite inferior diferente si la matriz se va a usar con otros lenguajes, como Visual Basic.

El límite superior depende del número de elementos y del valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente en 9.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
