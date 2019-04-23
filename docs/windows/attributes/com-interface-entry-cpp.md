---
title: COM_INTERFACE_ENTRY (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 65d174679f851613e064568b071cfcbdad8f0f06
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030412"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

Agrega una entrada de la interfaz en el mapa COM de la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parámetros

*com_interface_entry*<br/>
Una cadena que contiene el texto real de la entrada. Para obtener una lista de valores posibles, vea [Macros COM_INTERFACE_ENTRY](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Comentarios

El **com_interface_entry** C++ atributo inserta el contenido íntegra de una cadena de caracteres en el mapa de interfaz COM del objeto de destino. Si el atributo se aplica una vez al objeto de destino, se inserta la entrada en el principio de la asignación de interfaz existente. Si se aplica el atributo varias veces al mismo objeto de destino, las entradas se insertan al principio de la asignación de interfaz en el orden en que se reciben.

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

Dado que el primer uso de **com_interface_entry** hace que la nueva interfaz va a insertar al principio de la asignación de interfaz, debe ser uno de los siguientes tipos COM_INTERFACE_ENTRY:

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Usos adicionales de la **com_interface_entry** atributo puede usar todos los COM_INTERFACE_ENTRY tipos compatibles.

Esta restricción es necesaria porque ATL usa la primera entrada en el mapa de interfaz como identidad `IUnknown`; por lo tanto, la entrada debe ser una interfaz válida. Por ejemplo, el siguiente ejemplo de código no es válido porque la primera entrada en el mapa de interfaz no especifica una interfaz COM real.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Ejemplo

El código siguiente agrega dos entradas para el mapa de interfaz COM existente de `CMyBaseClass`. El primero es una interfaz estándar, y oculta el segundo el `IDebugTest` interfaz.

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

El mapa de objetos COM resultante para `CMyBaseClass` es como sigue:

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
|**Atributos requeridos**|Una o varias de las siguientes acciones: `coclass`, `progid`, o `vi_progid`.|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)