---
title: ms_union (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ms_union
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
ms.openlocfilehash: 26207c3c2c20fb039eb39e26f4d24e141c4dff07
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514368"
---
# <a name="ms_union"></a>ms_union

Controla la alineación de la representación de datos de red de las uniones no encapsuladas.

## <a name="syntax"></a>Sintaxis

```cpp
[ms_union]
```

## <a name="remarks"></a>Comentarios

El atributo **ms_union** C++ tiene la misma funcionalidad que el atributo MIDL [ms_union](/windows/win32/Midl/ms-union-attrib) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra la posición de **ms_union**:

```cpp
// cpp_attr_ref_ms_union.cpp
// compile with: /LD
#include <unknwn.h>
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl {
   HRESULT DisplayString([in, string] char * p1);
};

[export, switch_type(short)] union _WILLIE_UNION_TYPE  {
   [case(24)]
      float fMays;
   [case(25)]
      double dMcCovey;
   [default]
      int x;
};

[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Uniones no encapsuladas|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`dispinterface`|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)