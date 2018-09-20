---
title: context_self_unblock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
dev_langs:
- C++
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36bfc6053ddbfb68598e1465896f94bb0a895f1b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435901"
---
# <a name="contextselfunblock-class"></a>context_self_unblock (Clase)

Esta clase describe una excepción que se produce cuando se llama al método `Unblock` de un objeto `Context` desde el mismo contexto. Esto indicaría que un contexto especificado ha intentado desbloquearse a sí mismo.

## <a name="syntax"></a>Sintaxis

```
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[context_self_unblock](#ctor)|Sobrecargado. Construye un objeto `context_self_unblock`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`context_self_unblock`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> context_self_unblock)

Construye un objeto `context_self_unblock`.

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
