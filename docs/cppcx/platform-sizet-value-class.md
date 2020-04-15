---
title: Platform::SizeT (Clase de valor)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322160"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT (Clase de valor)

Representa el tamaño de un objeto. SizeT es un tipo de datos sin signo.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Miembros

|Member|Descripción|
|------------|-----------------|
|[SizeT::SizeT (Constructor)](#ctor)|Inicializa una nueva instancia de la clase con el valor especificado.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Metadatos:** platform.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>SizeT::SizeT constructor

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

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
