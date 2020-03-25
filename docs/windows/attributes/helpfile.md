---
title: HelpFile (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 1f928fa281c99630ad52ce1fde184c44e9387263
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166983"
---
# <a name="helpfile"></a>helpfile

Establece el nombre del archivo de ayuda para una biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Nombre del archivo que contiene los temas de ayuda.

## <a name="remarks"></a>Observaciones

El atributo **HelpFile** C++ tiene la misma funcionalidad que el atributo MIDL de [HelpFile](/windows/win32/Midl/helpfile) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [módulo](module-cpp.md) para obtener un ejemplo de cómo usar **HelpFile**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **typedef**, **Class**, Method, **Property**|
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
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
