---
title: exclusivo (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.unique
dev_langs:
- C++
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca5d2da5dc06b1cdf0e999939fcb110608ff3359
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062696"
---
# <a name="unique-c"></a>unique (C++)

Especifica un puntero único.

## <a name="syntax"></a>Sintaxis

```cpp
[unique]
```

## <a name="remarks"></a>Comentarios

El **único** atributo de C++ tiene la misma funcionalidad que el [único](/windows/desktop/Midl/unique) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte la [ref](ref-cpp.md) ejemplo para un ejemplo de uso de **único**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**TypeDef**, **struct**, **unión**, parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)