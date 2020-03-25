---
title: Interfaz Platform::IDisposable
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: 0024edbad0bb3311a0497be67fc8bcfc954602e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214245"
---
# <a name="platformidisposable-interface"></a>Interfaz Platform::IDisposable

Se utiliza para liberar recursos no administrados.

## <a name="syntax"></a>Sintaxis

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Atributos

**GuidAttribute**("de0cbaea-8065-4a45-B196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Members

La interfaz IDisposable hereda de la interfaz IUnknown. IDisposable también tiene los siguientes tipos de miembros:

**Métodos**

La interfaz IDisposable tiene los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|Dispose|Se utiliza para liberar recursos no administrados.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma
