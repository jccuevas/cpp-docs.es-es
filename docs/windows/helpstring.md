---
title: helpstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2892f957cf8937b5b030e7624bf3e39f546a7103
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437617"
---
# <a name="helpstring"></a>helpstring

Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstring(
   "string"
) ]
```

### <a name="parameters"></a>Parámetros

*string*<br/>
El texto de la cadena de ayuda.

## <a name="remarks"></a>Comentarios

El **helpstring** atributo de C++ tiene la misma funcionalidad que el [helpstring](/windows/desktop/Midl/helpstring) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [defaultvalue](../windows/defaultvalue.md) para obtener un ejemplo de cómo usar **helpstring**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, propiedad|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de interfaz](../windows/interface-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](../windows/helpfile.md)<br/>
[helpcontext](../windows/helpcontext.md)  