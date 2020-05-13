---
title: PROPPUT (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 8817d0042c3055b5bbf9b111e6f02b9d9a4c152c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166450"
---
# <a name="propput"></a>propput

Especifica una función de valor de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propput]
```

## <a name="remarks"></a>Observaciones

El atributo **PROPPUT** C++ tiene la misma funcionalidad que el atributo MIDL de [PROPPUT](/windows/win32/Midl/propput) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de uso de **PROPPUT**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`propget`, `propputref`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
