---
title: cancellation_token_source (clase)
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 131c4155ad902221d14f90f750f89c31479e2067
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142229"
---
# <a name="cancellation_token_source-class"></a>cancellation_token_source (clase)

La clase `cancellation_token_source` representa la capacidad para cancelar una operación que se puede cancelar.

## <a name="syntax"></a>Sintaxis

```cpp
class cancellation_token_source;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancellation_token_source](#ctor)|Sobrecargado. Construye un nuevo `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.|
|[~ cancellation_token_source destructor](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancel](#cancel)|Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.|
|[create_linked_source](#create_linked_source)|Sobrecargado. Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.|
|[get_token](#get_token)|Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`cancellation_token_source`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplcancellation_token. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ cancellation_token_source

```cpp
~cancellation_token_source();
```

## <a name="cancel"></a>Cancelar

Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.

```cpp
void cancel() const;
```

## <a name="ctor"></a>cancellation_token_source

Construye un nuevo `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.

```cpp
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Objeto que se va a copiar o quitar.

## <a name="create_linked_source"></a>create_linked_source

Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.

```cpp
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>Parámetros

*_Iter*<br/>
Tipo de iterador.

*_Src*<br/>
Token cuya cancelación provocará la cancelación del origen del token devuelto. Observe que el origen del token devuelto también se puede cancelar independientemente del origen incluido en este parámetro.

*_Begin*<br/>
Iterador de la biblioteca C++ estándar que corresponde al principio del intervalo de tokens cuya cancelación se va a escuchar.

*_End*<br/>
Iterador de la biblioteca C++ estándar correspondiente al final del intervalo de tokens cuya cancelación se va a escuchar.

### <a name="return-value"></a>Valor devuelto

`cancellation_token_source` que se cancela cuando se cancela el token proporcionado por el parámetro `_Src`.

## <a name="get_token"></a>get_token

Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.

```cpp
cancellation_token get_token() const;
```

### <a name="return-value"></a>Valor devuelto

Token de cancelación asociado a este origen.

## <a name="operator_neq"></a>operador! =

```cpp
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Operando.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq"></a>operador =

```cpp
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Operando.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq_eq"></a>operador = =

```cpp
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Operando.

### <a name="return-value"></a>Valor devuelto

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
