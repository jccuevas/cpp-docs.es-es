---
title: PTR (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: 2c712a2d9c85e0fe8fd8c4dbad5c7f48812ab1a2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030133"
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

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (Atributos)](typedef-enum-union-and-struct-attributes.md)