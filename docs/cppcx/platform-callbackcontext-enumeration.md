---
title: Platform::CallbackContext (Enumeración)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 1daa3988fcb985dab9d3083233a3703a20cc2fdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214294"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext (Enumeración)

Especifica el contexto del subproceso en el que se ejecuta una función de devolución de llamada (controlador de eventos).

## <a name="syntax"></a>Sintaxis

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Members

|Código de tipo|Descripción|
|---------------|-----------------|
|Any|La función de devolución de llamada se puede ejecutar en cualquier contexto de subproceso.|
|Iguales|La función de devolución de llamada solo se puede ejecutar en el contexto de subproceso que inició la operación asincrónica.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd
