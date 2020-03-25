---
title: HelpContext (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 292db21e8092284a92b09ef3f889bb0475d0d886
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167009"
---
# <a name="helpcontext"></a>helpcontext

Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de **ayuda** .

## <a name="syntax"></a>Sintaxis

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parámetros

*id*<br/>
IDENTIFICADOR de contexto del tema de ayuda. Vea [la ayuda HTML: ayuda contextual para los programas](../../mfc/html-help-context-sensitive-help-for-your-programs.md) para obtener más información sobre los identificadores de contexto.

## <a name="remarks"></a>Observaciones

El atributo **HelpContext** C++ tiene la misma funcionalidad que el atributo MIDL de [HelpContext](/windows/win32/Midl/helpcontext) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [DefaultValue](defaultvalue.md) para obtener un ejemplo de cómo utilizar **HelpContext**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **typedef**, **Class**, Method, Property|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
