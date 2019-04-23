---
title: DefaultValue (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvalue
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
ms.openlocfilehash: ff6924db6f4805bb5f2dbab69076a86020b2a075
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026323"
---
# <a name="defaultvalue"></a>defaultvalue

Permite especificar un valor predeterminado para un parámetro opcional con tipo.

## <a name="syntax"></a>Sintaxis

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>Parámetros

*value*<br/>
El valor predeterminado para el parámetro.

## <a name="remarks"></a>Comentarios

El **defaultvalue** atributo de C++ tiene la misma funcionalidad que el [defaultvalue](/windows/desktop/Midl/defaultvalue) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra un método de interfaz mediante el **defaultvalue** atributo:

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"), dual, oleautomation, helpstring("IFireTabCtrl Interface"), helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",    version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[out](out-cpp.md)<br/>
[retval](retval.md)<br/>
[in](in-cpp.md)<br/>
[pointer_default](pointer-default.md)<br/>
[unique](unique-cpp.md)