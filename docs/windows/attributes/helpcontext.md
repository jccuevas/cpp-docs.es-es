---
title: HelpContext (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 22023b4087c67b62d540d021fa06fd3582c7e4e2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038179"
---
# <a name="helpcontext"></a>helpcontext

Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el **ayuda** archivo.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parámetros

*id*<br/>
Identificador de contexto del tema de ayuda. Consulte [ayuda HTML: Ayuda contextual para los programas](../../mfc/html-help-context-sensitive-help-for-your-programs.md) para obtener más información sobre identificadores de contexto.

## <a name="remarks"></a>Comentarios

El **helpcontext** atributo de C++ tiene la misma funcionalidad que el [helpcontext](/windows/desktop/Midl/helpcontext) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [defaultvalue](defaultvalue.md) para obtener un ejemplo de cómo usar **helpcontext**.

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
[helpstring](helpstring.md)