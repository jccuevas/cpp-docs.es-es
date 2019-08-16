---
title: HelpFile (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 538cdbb38ac525cfee03a641f3e62e22a69f8e2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501550"
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

## <a name="remarks"></a>Comentarios

El atributo **HelpFile** C++ tiene la misma funcionalidad que el atributo MIDL de [HelpFile](/windows/win32/Midl/helpfile) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [módulo](module-cpp.md) para obtener un ejemplo de cómo usar **HelpFile**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **typedef**, **Class**, Method, **Property**|
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
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)