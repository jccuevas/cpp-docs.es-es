---
title: iid_is (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 176ab83bfae18ff7f43fe0860591f2d1ac50d7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535335"
---
# <a name="iidis"></a>iid_is

Especifica el IID de la interfaz COM que apunta a un puntero de interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*Expresión*<br/>
Una expresión del lenguaje C que especifica un IID de interfaz COM que apunta un puntero de interfaz.

## <a name="remarks"></a>Comentarios

El **iid_is** atributo de C++ tiene la misma funcionalidad que el [iid_is](/windows/desktop/Midl/iid-is) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra el uso de **iid_is**:

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)