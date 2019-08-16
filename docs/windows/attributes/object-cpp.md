---
title: objeto (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407541"
---
# <a name="object-c"></a>object (C++)

Identifica una interfaz personalizada.

## <a name="syntax"></a>Sintaxis

```cpp
[object]
```

## <a name="remarks"></a>Comentarios

Cuando precede a una definición de interfaz, el **objeto** la interfaz que se colocarán en el archivo .idl como una interfaz personalizada hace que el atributo de C++.

Cualquier interfaz marcada con el objeto debe heredar de `IUnknown`. Esta condición se cumple si cualquiera de las interfaces bases se hereda de `IUnknown`. Si no hay interfaces bases se heredan de `IUnknown`, el compilador hará que la interfaz marcada con **objeto** derivar `IUnknown`.

## <a name="example"></a>Ejemplo

Consulte [nonbrowsable](nonbrowsable.md) para obtener un ejemplo de cómo usar **objeto**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)