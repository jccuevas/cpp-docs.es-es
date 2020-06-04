---
title: com_interface_entry (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: d7b378baedd3f8c2720c7ab17698e8b416304061
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168309"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

Agrega una entrada de interfaz en el mapa COM de la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parámetros

*com_interface_entry*<br/>
Cadena que contiene el texto real de la entrada. Para obtener una lista de los valores posibles, vea [macros COM_INTERFACE_ENTRY](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Observaciones

El atributo **COM_INTERFACE_ENTRY** C++ inserta el contenido no simplificado de una cadena de caracteres en el mapa de interfaz com del objeto de destino. Si el atributo se aplica una vez al objeto de destino, la entrada se inserta en el principio del mapa de interfaz existente. Si el atributo se aplica varias veces al mismo objeto de destino, las entradas se insertan al principio del mapa de interfaz en el orden en que se reciben.

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica `progid`, también se aplican `vi_progid` y `coclass`.

Dado que el primer uso de **COM_INTERFACE_ENTRY** hace que la nueva interfaz se inserte al principio del mapa de interfaz, debe ser uno de los siguientes tipos de COM_INTERFACE_ENTRY:

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Los usos adicionales del atributo **COM_INTERFACE_ENTRY** pueden utilizar todos los tipos de COM_INTERFACE_ENTRY admitidos.

Esta restricción es necesaria porque ATL usa la primera entrada en el mapa de interfaz como `IUnknown`de identidad; por lo tanto, la entrada debe ser una interfaz válida. Por ejemplo, el siguiente ejemplo de código no es válido porque la primera entrada del mapa de interfaz no especifica una interfaz COM real.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Ejemplo

En el código siguiente se agregan dos entradas al mapa de interfaz COM existente de `CMyBaseClass`. La primera es una interfaz estándar y la segunda oculta la interfaz `IDebugTest`.

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

La asignación de objeto COM resultante para `CMyBaseClass` es la siguiente:

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sí|
|**Atributos requeridos**|Uno o varios de los siguientes: `coclass`, `progid`o `vi_progid`.|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)
