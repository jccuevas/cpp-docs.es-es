---
title: HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 66cd89c28ea01c3a75d0cb25aa6f96a234e379b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418208"
---
# <a name="helpfile"></a>helpfile

Establece el nombre del archivo de ayuda para una biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
El nombre del archivo que contiene los temas de ayuda.

## <a name="remarks"></a>Comentarios

El **helpfile** atributo de C++ tiene la misma funcionalidad que el [helpfile](/windows/desktop/Midl/helpfile) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [módulo](../windows/module-cpp.md) para obtener un ejemplo de cómo usar **helpfile**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, **propiedad**|
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
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)  