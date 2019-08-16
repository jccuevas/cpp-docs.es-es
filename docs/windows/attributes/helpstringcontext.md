---
title: helpstringcontext (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: ae48c6216b1f1d987b33eff50acf9d82dc551400
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501489"
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

## <a name="remarks"></a>Comentarios

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[module](module-cpp.md)