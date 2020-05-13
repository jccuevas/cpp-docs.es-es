---
title: defaultcollelem
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultcollelem
helpviewer_keywords:
- defaultcollelem attribute
ms.assetid: 3dbbd293-8b83-4f70-a36b-64cc1d0b6713
ms.openlocfilehash: 048d2933b8c024e74511e6cb49ae5c3240f3e710
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167126"
---
# <a name="defaultcollelem"></a>defaultcollelem

Se usa para Visual Basic la optimización del código.

## <a name="syntax"></a>Sintaxis

```cpp
[defaultcollelem]
```

## <a name="remarks"></a>Observaciones

El atributo **defaultcollelem** C++ tiene la misma funcionalidad que el atributo MIDL [defaultcollelem](/windows/win32/Midl/defaultcollelem) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un método de interfaz mediante el atributo **defaultcollelem** :

```cpp
// cpp_attr_ref_defaultcollelem.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyForm
{
   [propget, id(1), bindable, defaultcollelem, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, defaultcollelem, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)
