---
title: unsupported_os (Clase)
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 8277827aa8713ef57731a3e0da0898829b9fa9fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186371"
---
# <a name="unsupportedos-class"></a>unsupported_os (Clase)

Esta clase describe una excepción que se produce cuando se usa un sistema operativo no compatible.

## <a name="syntax"></a>Sintaxis

```
class unsupported_os : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[unsupported_os](#ctor)|Sobrecargado. Construye un objeto `unsupported_os`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`unsupported_os`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> unsupported_os

Construye un objeto `unsupported_os`.

```
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
