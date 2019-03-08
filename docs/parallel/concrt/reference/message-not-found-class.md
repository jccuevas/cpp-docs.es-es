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
ms.openlocfilehash: da0a44b90346959756c1ef7c685bef234fe6e46a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296688"
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

##  <a name="ctor"></a> message_not_found

Construye un objeto `message_not_found`.

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)
