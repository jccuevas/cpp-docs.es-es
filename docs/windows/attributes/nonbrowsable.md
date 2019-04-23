---
title: nonbrowsable (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonbrowsable
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
ms.openlocfilehash: 0a5e01c0fde49c7debb7749f5a1d148acb9cca6f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038413"
---
# <a name="nonbrowsable"></a>nonbrowsable

Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>Comentarios

El **nonbrowsable** atributo de C++ tiene la misma funcionalidad que el [nonbrowsable](/windows/desktop/Midl/nonbrowsable) atributo MIDL.

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)