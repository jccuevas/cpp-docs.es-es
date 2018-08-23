---
title: switch_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28501c0105ce9d62c72dc9013b881029f4bc8bfb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590671"
---
# <a name="switchtype"></a>switch_type

Identifica el tipo de la variable utilizada como la unión discriminante.

## <a name="syntax"></a>Sintaxis

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parámetros

*type*  
El tipo de conmutador, puede ser un tipo entero, carácter, un valor booleano o enumeración.

## <a name="remarks"></a>Comentarios

El **switch_type** atributo de C++ tiene la misma funcionalidad que el [switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) atributo MIDL.

Atributos de C++ no admiten [encapsulado uniones](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Uniones nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) solo se admiten en el formato siguiente:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Ejemplo

Consulte la [caso](../windows/case-cpp.md) ejemplo para un ejemplo de uso de **switch_type**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**typedef**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)  
[export](../windows/export.md)  