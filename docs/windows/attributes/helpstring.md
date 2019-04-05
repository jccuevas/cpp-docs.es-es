---
title: helpstring (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 623b2c7fb4ce7c3e5de87d21f012d008720fdee2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022210"
---
# <a name="helpstring"></a>helpstring

Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parámetros

*cadena*<br/>
El texto de la cadena de ayuda.

## <a name="remarks"></a>Comentarios

El **helpstring** atributo de C++ tiene la misma funcionalidad que el [helpstring](/windows/desktop/Midl/helpstring) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [defaultvalue](defaultvalue.md) para obtener un ejemplo de cómo usar **helpstring**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, propiedad|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (Atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)