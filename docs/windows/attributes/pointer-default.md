---
title: pointer_default (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: d0c5832623c1e418f4c6e8bdb606d1d363503483
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166541"
---
# <a name="pointer_default"></a>pointer_default

Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.

## <a name="syntax"></a>Sintaxis

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Valor que describe el tipo de puntero: **ptr**, **ref**o **único**.

## <a name="remarks"></a>Observaciones

El atributo **pointer_default** C++ tiene la misma funcionalidad que el atributo MIDL [pointer_default](/windows/win32/Midl/pointer-default) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [DefaultValue](defaultvalue.md) para obtener un ejemplo de uso de **pointer_default**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)
