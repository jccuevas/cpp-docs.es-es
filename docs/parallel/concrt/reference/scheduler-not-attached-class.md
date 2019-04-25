---
title: scheduler_not_attached (Clase)
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: be8a04c7cf6ef5aa4d6070e92df14e643395ef00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160125"
---
# <a name="schedulernotattached-class"></a>scheduler_not_attached (Clase)

Esta clase describe una excepción que se produce cuando se realiza una operación que requiere que un programador se adjunte al contexto actual y no hay ninguno.

## <a name="syntax"></a>Sintaxis

```
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|Sobrecargado. Construye un objeto `scheduler_not_attached`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> scheduler_not_attached

Construye un objeto `scheduler_not_attached`.

```
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
