---
title: helpstringcontext (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: 339d65070efe8bf2dafae2cf76e92c75a1bebc18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168154"
---
# <a name="helpstringcontext"></a>helpstringcontext

Especifica el identificador de un tema de ayuda en un archivo. hlp o. chm.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parámetros

*contextID*<br/>
Un identificador de contexto de ayuda de 32 bits en el archivo de **ayuda** .

## <a name="remarks"></a>Observaciones

El atributo **helpstringcontext** C++ tiene la misma funcionalidad que el atributo ODL de [helpstringcontext](/windows/win32/Midl/helpstringcontext) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[module](module-cpp.md)
