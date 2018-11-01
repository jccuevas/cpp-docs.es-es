---
title: dispinterface (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: d0ace76fdbbc1ff930bccb4e6fc203895b4f1637
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677284"
---
# <a name="dispinterface"></a>dispinterface

Coloca una interfaz en el archivo .idl como interfaz de envío.

## <a name="syntax"></a>Sintaxis

```cpp
[dispinterface]
```

## <a name="remarks"></a>Comentarios

Cuando el atributo de C++ **dispinterface** precede a una interfaz, hace que esta se coloque dentro del bloque de biblioteca del archivo .idl generado.

A menos que especifique una clase base, se derivará una interfaz de envío de `IDispatch`. Debe especificar un [id](id.md) para los miembros de una interfaz de envío.

El ejemplo de uso de [dispinterface](/windows/desktop/Midl/dispinterface) en la documentación de MIDL:

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos por uso](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)