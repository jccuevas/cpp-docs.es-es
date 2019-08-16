---
title: propget (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 044562ba870d6e36ddfcec0c7e84253b111a9eea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514210"
---
# <a name="propget"></a>propget

Especifica una función de descriptor de acceso de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propget]
```

## <a name="remarks"></a>Comentarios

El atributo **propget** C++ tiene la misma funcionalidad que el atributo de MIDL [propget](/windows/win32/Midl/propget) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de uso de **propget**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`propput`, `propputref`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)