---
title: message_not_found (Clase)
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: 7b6bd33e69d24e452414b2537ad70bf31e6b722f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458479"
---
# <a name="messagenotfound-class"></a>message_not_found (Clase)

Esta clase describe una excepción que se produce cuando un bloque de mensajería no puede encontrar un mensaje solicitado.

## <a name="syntax"></a>Sintaxis

```
class message_not_found : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[message_not_found](#ctor)|Sobrecargado. Construye un objeto `message_not_found`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`message_not_found`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> message_not_found)

Construye un objeto `message_not_found`.

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)

