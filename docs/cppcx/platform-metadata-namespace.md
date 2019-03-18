---
title: Platform::Metadata (Espacio de nombres)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
ms.openlocfilehash: 9626b3a9d28d28fd52a0d2295af8fda8855cd90c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739453"
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata (Espacio de nombres)

Este espacio de nombres contiene atributos que modifican las declaraciones de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Platform {
   namespace Metadata {
}}
```

### <a name="members"></a>Miembros

Aunque este espacio de nombres está previsto para uso interno, los exploradores pueden mostrar los siguientes miembros de este espacio de nombres.

|nombre|Observación|
|----------|------------|
|Atributo|La clase base de los atributos.|
|[Platform::Metadata::DefaultMemberAttribute (Atributo)](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Indica la función preferida que se va a invocar entre varias funciones sobrecargadas posibles.|
|[Atributo Platform::Metadata::FlagsAttribute](../cppcx/platform-metadata-flagsattribute-attribute.md)Flags|Declara una enumeración como enumeración de campos de bits.<br /><br /> En el siguiente ejemplo se muestra cómo aplicar el atributo `Flags` a una enumeración.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Garantiza que una clase ref privada tiene un nombre de clase en tiempo de ejecución válido.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Platform`

### <a name="requirements"></a>Requisitos

**Metadatos:** platform.winmd

**Espacio de nombres**: Platform:: Metadata

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)
