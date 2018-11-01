---
title: pragma (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: d90e37e27f7e2a13ffebd11043e415c1d43751c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430504"
---
# <a name="pragma"></a>pragma

Emite la cadena especificada en el archivo .idl generado sin el uso de comillas.

## <a name="syntax"></a>Sintaxis

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Parámetros

*pragma_statement*<br/>
La pragma que desea entrar en el archivo .idl generado.

## <a name="remarks"></a>Comentarios

El **pragma** atributo de C++ tiene la misma funcionalidad que el [pragma](/windows/desktop/Midl/pragma) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)