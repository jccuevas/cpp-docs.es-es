---
title: noncreatable (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: e855497cb6f619ecdaa6aedf16a04f045a60faa7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514567"
---
# <a name="noncreatable"></a>noncreatable

Define un objeto del que no se pueden crear instancias de sí mismo.

## <a name="syntax"></a>Sintaxis

```cpp
[noncreatable]
```

## <a name="remarks"></a>Comentarios

El C++ atributo **noncreatable** tiene la misma funcionalidad que el atributo MIDL no [creatable](/windows/win32/Midl/noncreatable) y se pasa automáticamente a la generada. Archivo IDL del compilador.

Cuando este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambia. Además del comportamiento anterior, el atributo también inserta la macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) . Esta macro indica a ATL que el objeto no se puede crear externamente.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
