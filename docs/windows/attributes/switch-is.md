---
title: switch_is (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_is
dev_langs:
- C++
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 425caf89619670dd8cabe647b01f8df63be24167
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792166"
---
# <a name="switchis"></a>switch_is

Especifica la expresión o el identificador que actúa como la unión discriminante que selecciona al miembro de unión.

## <a name="syntax"></a>Sintaxis

```cpp
[switch_is]
```

## <a name="remarks"></a>Comentarios

El **switch_is** atributo de C++ tiene la misma funcionalidad que el [switch_is](/windows/desktop/Midl/switch-is) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte la [caso](case-cpp.md) ejemplo para un ejemplo de uso de **switch_is**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**typedef**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)  