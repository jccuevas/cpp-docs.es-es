---
title: iid_is (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 627ecff4835386dc70a9f3dfac0500404a84eefe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167997"
---
# <a name="iid_is"></a>iid_is

Especifica el IID de la interfaz COM a la que apunta un puntero de interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
Expresión del lenguaje C que especifica un IID de una interfaz COM apuntada por un puntero de interfaz.

## <a name="remarks"></a>Observaciones

El atributo **iid_is** C++ tiene la misma funcionalidad que el atributo MIDL [iid_is](/windows/win32/Midl/iid-is) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el uso de **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, miembro de datos|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)
