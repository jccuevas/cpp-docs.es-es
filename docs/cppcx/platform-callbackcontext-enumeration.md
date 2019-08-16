---
title: Platform::CallbackContext (Enumeración)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161685"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext (Enumeración)

Especifica el contexto del subproceso en el que se ejecuta una función de devolución de llamada (controlador de eventos).

## <a name="syntax"></a>Sintaxis

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Miembros

|Código de tipo|Descripción|
|---------------|-----------------|
|Cualquiera|La función de devolución de llamada se puede ejecutar en cualquier contexto de subproceso.|
|Igual|La función de devolución de llamada solo se puede ejecutar en el contexto de subproceso que inició la operación asincrónica.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd