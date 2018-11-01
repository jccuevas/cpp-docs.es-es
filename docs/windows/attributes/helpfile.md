---
title: HelpFile (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45ecd90dbad7c49dc6563acd7a78ae179403c240
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075182"
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