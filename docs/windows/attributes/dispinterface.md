---
title: dispinterface (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 66567b0a1b043136e0a754e3a52bbdd7c463e178
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168244"
---
# <a name="dispinterface"></a>dispinterface

Coloca una interfaz en el archivo .idl como interfaz de envío.

## <a name="syntax"></a>Sintaxis

```cpp
[dispinterface]
```

## <a name="remarks"></a>Observaciones

Cuando el atributo de C++ **dispinterface** precede a una interfaz, hace que esta se coloque dentro del bloque de biblioteca del archivo .idl generado.

A menos que especifique una clase base, se derivará una interfaz de envío de `IDispatch`. Debe especificar un [id](id.md) para los miembros de una interfaz de envío.

El ejemplo de uso de [dispinterface](/windows/win32/Midl/dispinterface) en la documentación de MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

no es válido para el atributo **dispinterface** .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [bindable](bindable.md) para ver un ejemplo de cómo usar **dispinterface**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos por uso](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
