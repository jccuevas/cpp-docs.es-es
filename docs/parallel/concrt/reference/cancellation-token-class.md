---
title: cancellation_token (Clase)
ms.date: 11/04/2016
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
ms.openlocfilehash: 60028ce439dc344696bb3814efb74e0daa21f6ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522205"
---
# <a name="cancellationtoken-class"></a>cancellation_token (Clase)

La clase `cancellation_token` representa la capacidad para determinar si se ha solicitado la cancelación de alguna operación. Se puede asociar un determinado símbolo con un objeto `task_group`, `structured_task_group` o `task` para proporcionar una cancelación implícita. Este token también puede sondearse para la cancelación o puede hacer que se registre una devolución únicamente si se cancela el objeto `cancellation_token_source` asociado.

## <a name="syntax"></a>Sintaxis

```
class cancellation_token;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[cancellation_token)](#ctor)||
|[~ cancellation_token (destructor)](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.|
|[is_cancelable](#is_cancelable)|Devuelve una indicación de si este token se puede cancelar o no.|
|[is_canceled](#is_canceled)|Devuelve **true** si se ha cancelado el token.|
|[none](#none)|Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.|
|[register_callback](#register_callback)|Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`cancellation_token`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplcancellation_token.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~ cancellation_token

```
~cancellation_token();
```

##  <a name="ctor"></a> cancellation_token)

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Cancellation_token para copiar o mover.

##  <a name="deregister_callback"></a> deregister_callback

Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.

```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parámetros

*_Registration*<br/>
Objeto `cancellation_token_registration` que se corresponde con la devolución de llamada cuyo registro se va a cancelar. Este símbolo se debe haber devuelto anteriormente desde una llamada al método `register`.

##  <a name="is_cancelable"></a> is_cancelable

Devuelve una indicación de si este token se puede cancelar o no.

```
bool is_cancelable() const;
```

### <a name="return-value"></a>Valor devuelto

Indicación de si este token se puede cancelar o no.

##  <a name="is_canceled"></a> is_canceled

Devuelve **true** si se ha cancelado el token.

```
bool is_canceled() const;
```

### <a name="return-value"></a>Valor devuelto

El valor **true** si el token se ha cancelado; en caso contrario, el valor **false**.

##  <a name="none"></a> Ninguno

Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.

```
static cancellation_token none();
```

### <a name="return-value"></a>Valor devuelto

Token de cancelación que no puede cancelarse.

##  <a name="operator_neq"></a> operador! =

```
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token` que se va comparar.

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq"></a> operator=

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
El `cancellation_token` para asignar.

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq_eq"></a> operador ==

```
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token` que se va comparar.

### <a name="return-value"></a>Valor devuelto

##  <a name="register_callback"></a> register_callback

Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.

```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.

*_Func*<br/>
Objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.

### <a name="return-value"></a>Valor devuelto

Objeto `cancellation_token_registration` que se puede utilizar en el método `deregister` para cancelar el registro de una devolución de llamada previamente registrada y evitar que esta se realice. El método producirá una [invalid_operation](invalid-operation-class.md) excepción si se llama en un `cancellation_token` objeto que se creó utilizando el [cancellation_token:: None](#none) método.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
