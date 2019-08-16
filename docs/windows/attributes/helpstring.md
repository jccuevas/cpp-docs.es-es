---
title: HelpString (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 47a07ee94ad774bde46dce00ea46612fae3a4eca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490873"
---
# <a name="helpstring"></a>helpstring

Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parámetros

*string*<br/>
Texto de la cadena de ayuda.

## <a name="remarks"></a>Comentarios

El atributo **HelpString** C++ tiene la misma funcionalidad que el atributo MIDL de [HelpString](/windows/win32/Midl/helpstring) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [DefaultValue](defaultvalue.md) para obtener un ejemplo de cómo usar **HelpString**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **typedef**, **Class**, Method, Property|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)