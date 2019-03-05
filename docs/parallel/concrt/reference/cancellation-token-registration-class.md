---
title: cancellation_token_registration (Clase)
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: c6ca8061181ec057110282fa297666235e898ff6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270838"
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration (Clase)

La clase `cancellation_token_registration` representa una notificación de devolución de llamada de un objeto `cancellation_token`. Cuando el método `register` de un objeto `cancellation_token` se usa para recibir una notificación de cuándo se produce la cancelación, se devuelve un objeto `cancellation_token_registration` como identificador a la devolución de la llamada de modo que el llamador puede solicitar que ya no se realice una devolución de llamada específica a través del uso del método `deregister`.

## <a name="syntax"></a>Sintaxis

```
class cancellation_token_registration;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration (destructor)](#dtor)||

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`cancellation_token_registration`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplcancellation_token.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~cancellation_token_registration

```
~cancellation_token_registration();
```

##  <a name="ctor"></a> cancellation_token_registration)

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
El `cancellation_token_registration` para copiar o mover.

##  <a name="operator_neq"></a> operator!=

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>

  `cancellation_token_registration` que se va comparar.

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq"></a> operator=

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
El `cancellation_token_registration` para asignar.

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq_eq"></a> operador ==

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>

  `cancellation_token_registration` que se va comparar.

### <a name="return-value"></a>Valor devuelto

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
