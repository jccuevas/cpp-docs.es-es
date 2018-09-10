---
title: DefaultMemberAttribute (atributo) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
dev_langs:
- C++
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54959b293752ac0453ba383f86ab225e0b45e471
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107008"
---
# <a name="platformmetadatadefaultmemberattribute-attribute"></a>Platform::Metadata::DefaultMemberAttribute (Atributo)

Indica la función preferida que se va a invocar entre varias funciones sobrecargadas posibles.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class DefaultMember abstract : Attribute
```

## <a name="inheritance"></a>Herencia

[Platform::Object](../cppcx/platform-object-class.md)

[Platform::Metadata::Attribute](../cppcx/platform-metadata-attribute-attribute.md)

### <a name="remarks"></a>Comentarios

Aplica el atributo DefaultMember a un método que va a ser utilizado por una aplicación JavaScript.

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Platform::Metadata

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Platform::Metadata (Espacio de nombres)](../cppcx/platform-metadata-namespace.md)