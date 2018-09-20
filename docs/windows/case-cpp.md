---
title: caso (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6b610ce888e91ed8029c4166fa79a847d700dba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436525"
---
# <a name="case-c"></a>case (C++)

Puede usar con el [switch_type](../windows/switch-type.md) atributo en un **union**.

## <a name="syntax"></a>Sintaxis

```cpp
[ case(
   value
) ]
```

#### <a name="parameters"></a>Parámetros

*valor*<br/>
Un valor de entrada posibles para el que desea proporcionar un procesamiento. El tipo de **valor** puede ser uno de los siguientes tipos:

- `int`

- `char`

- `boolean`

- `enum`

o un identificador de este tipo.

## <a name="remarks"></a>Comentarios

El **caso** atributo de C++ tiene la misma funcionalidad que el **caso** atributo MIDL. Este atributo sólo se utiliza con el [switch_type](../windows/switch-type.md) atributo.

## <a name="example"></a>Ejemplo

El código siguiente muestra un uso de la **caso** atributo:

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Miembro de un **clase** o **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)  