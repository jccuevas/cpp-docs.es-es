---
title: CAdapt (clase)
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
ms.openlocfilehash: 39184e952475fa0f05a6fc25c433191ea22b5c16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260745"
---
# <a name="cadapt-class"></a>CAdapt (clase)

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

|Name|Descripción|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAdapt::operator const T &](#operator_const_t_amp)|Devuelve un **const** hacen referencia a `m_T`.|
|[CAdapt::operator T &](#operator_t_amp)|Devuelve una referencia a `m_T`.|
|[CAdapt::operator <](#operator_lt)|Compara un objeto de tipo adaptado con `m_T`.|
|[CAdapt::operator =](#operator_eq)|Asigna un objeto del tipo adaptado a `m_T`.|
|[CAdapt::operator ==](#operator_eq_eq)|Compara un objeto de tipo adaptado con `m_T`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Datos que se están adaptando.|

## <a name="remarks"></a>Comentarios

`CAdapt` es una plantilla sencilla que se usa para ajustar las clases que vuelven a definir el operador address-of (`operator &`) para devolver algo distinto de la dirección del objeto. Algunos ejemplos de este tipo de clases son `CComBSTR`, `CComPtr` y `CComQIPtr` de ATL y la clase compatible con COM del compilador, `_com_ptr_t`. Todas estas clases, vuelva a definir el operador address-of para devolver la dirección de uno de sus miembros de datos (una cadena BSTR en el caso de `CComBSTR`y un puntero de interfaz en el caso de las otras clases).

`CAdapt`del rol principal que se va a ocultar el operador address-of definido por la clase *T*, aunque mantiene las características de la clase adaptada. `CAdapt` cumple esta función manteniendo un miembro público, [m_T](#m_t), del tipo *T*y definiendo operadores de conversión, operadores de comparación y un constructor de copias para permitir que las especializaciones de `CAdapt` sea trata como si fueran objetos de tipo *T*.

La clase `CAdapt` del adaptador es útil porque algunas clases de estilo contenedor esperan poder obtener las direcciones de sus objetos contenidos utilizando el operador address-of. La nueva definición del operador address-of puede frustrar este requisito, lo que normalmente produce errores de compilación e impide el uso del tipo no adaptado con clases que esperan que “simplemente funcione”. `CAdapt` proporciona un mecanismo para evitar estos problemas.

Normalmente, utilizará `CAdapt` cuando desee almacenar objetos `CComBSTR`, `CComPtr`, `CComQIPtr` o `_com_ptr_t` en una clase de estilo contenedor. Esta solía ser necesario en los contenedores de la biblioteca de C++ estándar antes de la compatibilidad con C++11 estándar, pero los contenedores de la biblioteca C++11 estándar trabajan automáticamente con tipos que tienen un operador `operator&()` sobrecargado. La biblioteca estándar logra esto utilizando internamente [std::addressof](../../standard-library/memory-functions.md#addressof) para obtener las direcciones reales de objetos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

##  <a name="cadapt"></a>  CAdapt::CAdapt

Los constructores permiten a un objeto de adaptador sea construido, copiados de un objeto de tipo adaptado o copiado de otro objeto de adaptador de forma predeterminada.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una variable del tipo que se adapta para copiarse en el objeto de adaptador recién construido.

*rSrCA*<br/>
Un objeto de adaptador cuyos datos contenidos deben copiar (o mover) en el objeto de adaptador recién construido.

##  <a name="m_t"></a>  CAdapt::m_T

Contiene los datos que se adapta.

```
T m_T;
```

### <a name="remarks"></a>Comentarios

Esto **pública** miembro de datos se puede acceder de forma directa o indirecta con [operator const T &](#operator_const_t_amp) y [operador T &](#operator_t_amp).

##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;

Devuelve un **const** hacen referencia a la [m_T](#m_t) miembro, lo que el objeto de adaptador se traten como si fuese un objeto de tipo *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** hacen referencia a `m_T`.

##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;

Devuelve una referencia a la [m_T](#m_t) miembro, lo que el objeto de adaptador se traten como si fuese un objeto de tipo *T*.

```
operator T&();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a `m_T`.

##  <a name="operator_lt"></a>  CAdapt::operator &lt;

Compara un objeto de tipo adaptado con [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia al objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

El resultado de la comparación entre `m_T` y *rSrc*.

##  <a name="operator_eq"></a>  CAdapt::operator =

El operador de asignación asigna el argumento, *rSrc*, para el miembro de datos [m_T](#m_t) y devuelve el objeto de adaptador actual.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia a un objeto de tipo adaptado a copiarse.

*rSrCA*<br/>
Una referencia a un objeto que se va a mover.

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto actual.

##  <a name="operator_eq_eq"></a>  CAdapt::operator ==

Compara un objeto de tipo adaptado con [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia al objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

El resultado de la comparación entre *m_T* y *rSrc*.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
