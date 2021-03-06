---
title: String (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 96d5e609130b34a4a5f35109ce691c2de470e537
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166170"
---
# <a name="string-c"></a>string (C++)

Indica que la matriz **Char**, **wchar_t**, `byte` (o equivalente) unidimensional o el puntero a dicha matriz se deben tratar como una cadena.

## <a name="syntax"></a>Sintaxis

```cpp
[string]
```

## <a name="remarks"></a>Observaciones

El atributo de **cadena** C++ tiene la misma funcionalidad que el atributo MIDL de [cadena](/windows/win32/Midl/string) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar String en una interfaz y en una definición de **tipo** :

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Matriz o puntero a una matriz, parámetro de interfaz, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de matriz](array-attributes.md)<br/>
[export](export.md)
