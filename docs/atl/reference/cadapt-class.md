---
title: Clase CAdapt
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321638"
---
# <a name="cadapt-class"></a>Clase CAdapt

Esta plantilla se utiliza para ajustar las clases que vuelven a definir el operador address-of para devolver algo distinto de la dirección del objeto.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo adaptado.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAdapt::operator const T&](#operator_const_t_amp)|Devuelve una referencia **const** a `m_T`.|
|[CAdapt::operator T&](#operator_t_amp)|Devuelve una referencia a `m_T`.|
|[CAdapt::operador <](#operator_lt)|Compara un objeto de tipo adaptado con `m_T`.|
|[CAdapt::operador ?](#operator_eq)|Asigna un objeto del tipo adaptado a `m_T`.|
|[CAdapt::operador ?](#operator_eq_eq)|Compara un objeto de tipo adaptado con `m_T`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Datos que se están adaptando.|

## <a name="remarks"></a>Observaciones

`CAdapt` es una plantilla sencilla que se usa para ajustar las clases que vuelven a definir el operador address-of (`operator &`) para devolver algo distinto de la dirección del objeto. Algunos ejemplos de este tipo de clases son `CComBSTR`, `CComPtr` y `CComQIPtr` de ATL y la clase compatible con COM del compilador, `_com_ptr_t`. Todas estas clases redefinen el operador address-of para devolver la dirección de `CComBSTR`uno de sus miembros de datos (un BSTR en el caso de , y un puntero de interfaz en el caso de las otras clases).

`CAdapt`'s función principal es ocultar la dirección del operador definida por la clase *T*, pero conservando las características de la clase adaptada. `CAdapt`cumple este rol al tener un miembro público, [m_T](#m_t), de tipo *T*, y mediante la `CAdapt` definición de operadores de conversión, operadores de comparación y un constructor de copias para permitir que las especializaciones se traten como si fueran objetos de tipo *T.*

La clase `CAdapt` del adaptador es útil porque algunas clases de estilo contenedor esperan poder obtener las direcciones de sus objetos contenidos utilizando el operador address-of. La nueva definición del operador address-of puede frustrar este requisito, lo que normalmente produce errores de compilación e impide el uso del tipo no adaptado con clases que esperan que “simplemente funcione”. `CAdapt` proporciona un mecanismo para evitar estos problemas.

Normalmente, utilizará `CAdapt` cuando desee almacenar objetos `CComBSTR`, `CComPtr`, `CComQIPtr` o `_com_ptr_t` en una clase de estilo contenedor. Esta solía ser necesario en los contenedores de la biblioteca de C++ estándar antes de la compatibilidad con C++11 estándar, pero los contenedores de la biblioteca C++11 estándar trabajan automáticamente con tipos que tienen un operador `operator&()` sobrecargado. La biblioteca estándar logra esto mediante el uso interno de [std::addressof](../../standard-library/memory-functions.md#addressof) para obtener las direcciones verdaderas de los objetos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

Los constructores permiten que un objeto de adaptador se construya de forma predeterminada, se copie desde un objeto del tipo adaptado o se copie desde otro objeto de adaptador.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Variable del tipo que se va a adaptar para copiarse en el objeto de adaptador recién construido.

*rSrCA*<br/>
Un objeto de adaptador cuyos datos contenidos se deben copiar (o mover) en el objeto de adaptador recién construido.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt::m_T

Contiene los datos que se están adaptando.

```
T m_T;
```

### <a name="remarks"></a>Observaciones

Se puede acceder a este miembro de datos **públicos** directa o indirectamente con [el operador const T&](#operator_const_t_amp) y el operador T [&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt::operator const T&amp;

Devuelve una referencia **const** al miembro [m_T,](#m_t) lo que permite que el objeto adapter se trate como si fuera un objeto de tipo *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Valor devuelto

Una **referencia const** a `m_T`.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt::operador T&amp;

Devuelve una referencia al miembro [m_T,](#m_t) lo que permite que el objeto adapter se trate como si fuera un objeto de tipo *T*.

```
operator T&();
```

### <a name="return-value"></a>Valor devuelto

Referencia a una estructura `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::operador&lt;

Compara un objeto del tipo adaptado con [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia al objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

El resultado de `m_T` la comparación entre *rSrc y rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt::operador ?

El operador de asignación asigna el argumento, *rSrc*, al miembro de datos [m_T](#m_t) y devuelve el objeto de adaptador actual.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia a un objeto del tipo adaptado que se va a copiar.

*rSrCA*<br/>
Una referencia a un objeto que se va a mover.

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto actual.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt::operador ?

Compara un objeto del tipo adaptado con [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia al objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

El resultado de la comparación entre *m_T* y *rSrc*.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
