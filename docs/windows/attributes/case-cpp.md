---
title: caso (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 1e7a15d81c8efd5320cf142faa3e3f381f81abd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079680"
---
# <a name="case-c"></a>case (C++)

Puede usar con el [switch_type](switch-type.md) atributo en un **union**.

## <a name="syntax"></a>Sintaxis

```cpp
[ case(value) ]
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

El **caso** atributo de C++ tiene la misma funcionalidad que el **caso** atributo MIDL. Este atributo sólo se utiliza con el [switch_type](switch-type.md) atributo.

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

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)