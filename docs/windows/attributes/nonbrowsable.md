---
title: nonbrowsableable (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonbrowsable
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
ms.openlocfilehash: f0aae070c1c97695180797b228178b210493b7bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166567"
---
# <a name="nonbrowsable"></a>nonbrowsable

Indica que un miembro de interfaz no se debe mostrar en un explorador de propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>Observaciones

El **nonbrowsable** C++ atributo nonbrowsable tiene la misma funcionalidad que el atributo MIDL no [explorable](/windows/win32/Midl/nonbrowsable) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_nonbrowsable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, helpstring("help string"), helpstringcontext(1),
uuid="11111111-1111-1111-1111-111111111111"]
__interface IMyI
{
   [nonbrowsable] HRESULT xx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)
