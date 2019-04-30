---
title: cadena (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: e1b528fb922a15655de403c6099ee1d36e2fb3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407281"
---
# <a name="string-c"></a>string (C++)

Indica que unidimensional **char**, **wchar_t**, `byte` (o equivalentes) el puntero a este tipo de matriz o matriz debe tratarse como una cadena.

## <a name="syntax"></a>Sintaxis

```cpp
[string]
```

## <a name="remarks"></a>Comentarios

El **cadena** atributo de C++ tiene la misma funcionalidad que el [cadena](/windows/desktop/Midl/string) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar **cadena** en una interfaz y en una definición de tipo:

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
|**Se aplica a**|Matriz o puntero a una matriz, el parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de matriz](array-attributes.md)<br/>
[export](export.md)