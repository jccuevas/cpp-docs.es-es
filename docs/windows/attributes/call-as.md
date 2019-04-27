---
title: call_as (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: a0051cdca6673800b37d5733c0b849da24010fcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148359"
---
# <a name="callas"></a>call_as

Permite un [local](local-cpp.md) función a la que se asignan a una función remota para que cuando se llama a la función remota, se invoca la función local.

## <a name="syntax"></a>Sintaxis

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parámetros

*function*<br/>
La función local que desea que se llama cuando se invoca una función remota.

## <a name="remarks"></a>Comentarios

El **call_as** C++ atributo tiene la misma funcionalidad que el [call_as](/windows/desktop/Midl/call-as) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo puede usar **call_as** para asignar una función utilizables (`f1`) a una función remota (`Remf1`):

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
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
[Atributos de método](method-attributes.md)<br/>
[local](local-cpp.md)