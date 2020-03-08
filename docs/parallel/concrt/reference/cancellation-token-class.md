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
ms.openlocfilehash: 34743ce48510eec9d8f7862e5ed951a722932962
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876079"
---
# <a name="cancellation_token-class"></a>cancellation_token (Clase)

La clase `cancellation_token` representa la capacidad para determinar si se ha solicitado la cancelación de alguna operación. Se puede asociar un determinado símbolo con un objeto `task_group`, `structured_task_group` o `task` para proporcionar una cancelación implícita. Este token también puede sondearse para la cancelación o puede hacer que se registre una devolución únicamente si se cancela el objeto `cancellation_token_source` asociado.

## <a name="syntax"></a>Sintaxis

```cpp
class cancellation_token;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token destructor](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.|
|[is_cancelable](#is_cancelable)|Devuelve una indicación de si este token se puede cancelar o no.|
|[is_canceled](#is_canceled)|Devuelve **true** si el token se ha cancelado.|
|[Ninguna](#none)|Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.|
|[register_callback](#register_callback)|Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`cancellation_token`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplcancellation_token. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="ctor"></a>cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Cancellation_token que se va a copiar o a transferir.

## <a name="deregister_callback"></a>deregister_callback

Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parámetros

*_Registration*<br/>
Objeto `cancellation_token_registration` que se corresponde con la devolución de llamada cuyo registro se va a cancelar. Este símbolo se debe haber devuelto anteriormente desde una llamada al método `register`.

## <a name="is_cancelable"></a>is_cancelable

Devuelve una indicación de si este token se puede cancelar o no.

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>Valor devuelto

Indicación de si este token se puede cancelar o no.

## <a name="is_canceled"></a>is_canceled

Devuelve **true** si el token se ha cancelado.

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>Valor devuelto

El valor **true** si se ha cancelado el token; de lo contrario, el valor **es false**.

## <a name="none"></a>ninguna

Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>Valor devuelto

Token de cancelación que no puede cancelarse.

## <a name="operator_neq"></a>operador! =

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token` que se va comparar.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq"></a>operador =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token` que se va a asignar.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq_eq"></a>operador = =

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token` que se va comparar.

### <a name="return-value"></a>Valor devuelto

## <a name="register_callback"></a>register_callback

Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.

*_Func*<br/>
Objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.

### <a name="return-value"></a>Valor devuelto

Objeto `cancellation_token_registration` que se puede utilizar en el método `deregister` para cancelar el registro de una devolución de llamada previamente registrada y evitar que esta se realice. El método producirá una excepción de [invalid_operation](invalid-operation-class.md) si se llama en un objeto `cancellation_token` creado mediante el método [cancellation_token:: None](#none) .

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
