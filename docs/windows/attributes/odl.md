---
title: ODL (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: a4ae1aa7f27348e37c565b35e3dc0b2b1011c9cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514316"
---
# <a name="odl"></a>odl

Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL). El compilador MIDL no requiere el atributo **ODL** ; solo se reconoce por compatibilidad con archivos. ODL más antiguos.

## <a name="syntax"></a>Sintaxis

```cpp
[odl]
```

## <a name="remarks"></a>Comentarios

El atributo **ODL** C++ tiene la misma funcionalidad que el atributo MIDL de [ODL](/windows/win32/Midl/odl) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)