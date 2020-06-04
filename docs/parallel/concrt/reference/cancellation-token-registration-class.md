---
title: cancellation_token_registration (clase)
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142237"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration (clase)

La clase `cancellation_token_registration` representa una notificación de devolución de llamada de un objeto `cancellation_token`. Cuando el método `register` de un objeto `cancellation_token` se usa para recibir una notificación de cuándo se produce la cancelación, se devuelve un objeto `cancellation_token_registration` como identificador a la devolución de la llamada de modo que el llamador puede solicitar que ya no se realice una devolución de llamada específica a través del uso del método `deregister`.

## <a name="syntax"></a>Sintaxis

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration destructor](#dtor)||

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`cancellation_token_registration`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplcancellation_token. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token_registration` que se va a copiar o a quitar.

## <a name="operator_neq"></a>operador! =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`cancellation_token_registration` que se va comparar.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq"></a>operador =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
`cancellation_token_registration` que se va a asignar.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq_eq"></a>operador = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`cancellation_token_registration` que se va comparar.

### <a name="return-value"></a>Valor devuelto

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
