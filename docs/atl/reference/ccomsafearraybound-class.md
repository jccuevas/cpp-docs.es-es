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
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327383"
---
# <a name="ccomsafearraybound-class"></a>Clase CComSafeArrayBound

Esta clase es un contenedor para una estructura [SAFEARRAYBOUND.](/windows/win32/api/oaidl/ns-oaidl-safearraybound)

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
|[operador a la operadora de la red](#operator_eq)|Establece `CComSafeArrayBound` el valor en un nuevo valor.|

## <a name="remarks"></a>Observaciones

Esta clase es un `SAFEARRAYBOUND` contenedor para la estructura utilizada por [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Proporciona métodos para consultar y establecer los límites superior e `CComSafeArray` inferior de una única dimensión de un objeto y el número de elementos que contiene. Un `CComSafeArray` objeto multidimensional utiliza `CComSafeArrayBound` una matriz de objetos, uno para cada dimensión. Por lo tanto, al usar métodos como [GetCount](#getcount), tenga en cuenta que este método no devolverá el número total de elementos de una matriz multidimensional.

**Encabezado:** atlsafe.h

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

El constructor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos de la matriz.

*lLowerBound*<br/>
El límite inferior desde el que se numera la matriz.

### <a name="remarks"></a>Observaciones

Si se va a acceder a la matriz desde un programa C++, se recomienda que el límite inferior se defina como 0. Puede ser preferible usar un valor de límite inferior diferente si la matriz se va a usar con otros lenguajes, como Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArrayBound::GetCount

Llame a este método para devolver el número de elementos.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos.

### <a name="remarks"></a>Observaciones

Si el `CComSafeArray` objeto asociado representa una matriz multidimensional, este método solo devolverá el número total de elementos de la dimensión más a la derecha. Utilice [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) para obtener el número total de elementos.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

Llame a este método para devolver el límite inferior.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite `CComSafeArrayBound` inferior del objeto.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound

Llame a este método para devolver el límite superior.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite `CComSafeArrayBound` superior del objeto.

### <a name="remarks"></a>Observaciones

El límite superior depende del número de elementos y del valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente en 9.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArrayBound::operator ?

Establece `CComSafeArrayBound` el valor en un nuevo valor.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*Límite*<br/>
Objeto `CComSafeArrayBound` .

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `CComSafeArrayBound` al objeto.

### <a name="remarks"></a>Observaciones

El `CComSafeArrayBound` objeto se puede `CComSafeArrayBound`asignar utilizando un , o proporcionando el número de elementos, en cuyo caso el límite inferior se establece en 0 de forma predeterminada.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArrayBound::SetCount

Llame a este método para establecer el número de elementos.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de `CComSafeArrayBound` elementos del objeto.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Llame a este método para establecer el límite inferior.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parámetros

*lLowerBound*<br/>
El límite inferior.

### <a name="return-value"></a>Valor devuelto

Devuelve el nuevo límite `CComSafeArrayBound` inferior del objeto.

### <a name="remarks"></a>Observaciones

Si se va a tener acceso a la matriz desde un programa de Visual C++, se recomienda que el límite inferior se defina como 0. Puede ser preferible usar un valor de límite inferior diferente si la matriz se va a usar con otros lenguajes, como Visual Basic.

El límite superior depende del número de elementos y del valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente en 9.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
