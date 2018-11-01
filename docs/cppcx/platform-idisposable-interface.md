---
title: Platform::IDisposable (Interfaz)
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637442"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable (Interfaz)

Se utiliza para liberar recursos no administrados.

## <a name="syntax"></a>Sintaxis

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Atributos

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Miembros

La interfaz IDisposable hereda de la interfaz IUnknown. IDisposable también tiene los siguientes tipos de miembros:

**Métodos**

La interfaz IDisposable tiene los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|Desechar|Se utiliza para liberar recursos no administrados.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma