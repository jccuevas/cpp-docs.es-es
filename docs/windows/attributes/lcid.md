---
title: LCID (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 7c737661bb8429e416b515e4e7fcaf54956385d0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514539"
---
# <a name="lcid"></a>lcid

Permite pasar un identificador de configuración regional a una función.

## <a name="syntax"></a>Sintaxis

```cpp
[lcid]
```

## <a name="remarks"></a>Comentarios

El atributo **LCID** C++ implementa la funcionalidad del atributo MIDL de [LCID](/windows/win32/Midl/lcid) . Si desea implementar la configuración regional para un bloque de biblioteca, use el parámetro **LCID =** `lcid` para el atributo de [módulo](module-cpp.md) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)