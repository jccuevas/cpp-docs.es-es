---
title: noncreatable (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: a10d93650c0ae564019a09b34c3a604d12327998
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305325"
---
# <a name="noncreatable"></a>noncreatable

Define un objeto que no pueden crearse instancias por sí mismo.

## <a name="syntax"></a>Sintaxis

```cpp
[noncreatable]
```

## <a name="remarks"></a>Comentarios

El **noncreatable** atributo de C++ tiene la misma funcionalidad que el [noncreatable](/windows/desktop/Midl/noncreatable) atributo MIDL y se pasa automáticamente a generado. Archivo IDL por el compilador.

Cuando este atributo se utiliza dentro de un proyecto que usa ATL, cambia el comportamiento del atributo. Además del comportamiento anterior, el atributo también inserta la [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro. Esta macro se indica a ATL que el objeto no se puede crear externamente.

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
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
