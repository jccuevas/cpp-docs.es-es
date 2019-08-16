---
title: call_as (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: f36cf8d1be589cc614a6def583b00af00aabdb61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501805"
---
# <a name="call_as"></a>call_as

Habilita una función [local](local-cpp.md) que se va a asignar a una función remota para que cuando se llame a la función remota, se invoque la función local.

## <a name="syntax"></a>Sintaxis

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parámetros

*function*<br/>
Función local a la que se va a llamar cuando se invoque una función remota.

## <a name="remarks"></a>Comentarios

El atributo **call_as** C++ tiene la misma funcionalidad que el atributo MIDL [call_as](/windows/win32/Midl/call-as) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo se puede usar **call_as** para asignar una función`f1`no utilizables () a una función`Remf1`de uso remoto ():

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[local](local-cpp.md)