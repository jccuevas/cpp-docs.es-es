---
title: propget (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: d2c0ebab1630634ddd4fc81e7c9c8364f7fad46f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166464"
---
# <a name="propget"></a>propget

Especifica una función de descriptor de acceso de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propget]
```

## <a name="remarks"></a>Observaciones

El atributo **propget** C++ tiene la misma funcionalidad que el atributo de MIDL [propget](/windows/win32/Midl/propget) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de uso de **propget**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`propput`, `propputref`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)
