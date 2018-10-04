---
title: PTR (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89f00c5e2d65fde2c8a3bb2fd064796c2585c720
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792391"
---
# <a name="ptr"></a>ptr

Designa un puntero como un puntero completo.

## <a name="syntax"></a>Sintaxis

```cpp
[ptr]
```

## <a name="remarks"></a>Comentarios

El **ptr** atributo de C++ tiene la misma funcionalidad que el [ptr](/windows/desktop/Midl/ptr) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [defaultvalue](defaultvalue.md) para un ejemplo de uso de **ptr**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz, **(typedef)**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)  