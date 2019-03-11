---
title: Platform::SizeT (Clase de valor)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 7f81cb9e1fc2ef7a74cb3878c369e4d7d14e3d90
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751562"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT (Clase de valor)

Representa el tamaño de un objeto. SizeT es un tipo de datos sin signo.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Miembros

|Miembro|Descripción|
|------------|-----------------|
|[SizeT::SizeT (Constructor)](#ctor)|Inicializa una nueva instancia de la clase con el valor especificado.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a>  Constructor de Sizet

Inicializa una nueva instancia de SizeT con el valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parámetros

*value1*<br/>
Un valor sin signo de 32 bits.

*value2*<br/>
Puntero a un valor sin signo de 32 bits.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
