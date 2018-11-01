---
title: HelpFile (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 594ab4d02065e9b4efe1142c5ced9b76642e5481
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488054"
---
# <a name="helpfile"></a>helpfile

Establece el nombre del archivo de ayuda para una biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
El nombre del archivo que contiene los temas de ayuda.

## <a name="remarks"></a>Comentarios

El **helpfile** atributo de C++ tiene la misma funcionalidad que el [helpfile](/windows/desktop/Midl/helpfile) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [módulo](module-cpp.md) para obtener un ejemplo de cómo usar **helpfile**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, **propiedad**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)