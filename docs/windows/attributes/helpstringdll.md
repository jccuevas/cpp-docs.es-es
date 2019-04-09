---
title: helpstringdll (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 72f5926018e3ac7ec4770f83d7a2c3438b67d861
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025210"
---
# <a name="helpstringdll"></a>helpstringdll

Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Parámetros

*cadena*<br/>
DLL que se va a utilizar para realizar la búsqueda de cadenas de documento.

## <a name="remarks"></a>Comentarios

El **helpstringdll** atributo de C++ tiene la misma funcionalidad que el [helpstringdll](/windows/desktop/Midl/helpstringdll) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)