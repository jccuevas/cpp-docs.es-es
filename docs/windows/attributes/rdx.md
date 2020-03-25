---
title: RDX (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f0140b759b1d78eb1284213a0dc47d9600b2a83b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214635"
---
# <a name="rdx"></a>rdx

Crea una clave del registro o modifica una clave del registro existente.

## <a name="syntax"></a>Sintaxis

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Nombre de la clave que se va a crear o abrir.

*ValueName*<br/>
Opta Especifica el campo de valor que se va a establecer. Si un campo de valor con este nombre aún no existe en la clave, se agrega.

*regtype*<br/>
Tipo de clave del registro que se va a agregar. Puede ser uno de los siguientes: `text`, `dword`, `binary`o `CString`.

## <a name="remarks"></a>Observaciones

El atributo **RDX** C++ crea o modifica una clave del registro existente para un componente com. El atributo agrega una macro BEGIN_RDX_MAP al objeto que implementa el miembro de destino. `RegistryDataExchange`, una función insertada como resultado de la macro BEGIN_RDX_MAP, se puede utilizar para transferir datos entre el registro y los miembros de datos.

Este atributo se puede usar junto con los atributos [CoClass](coclass.md), [ProgID](progid.md)o [vi_progid](vi-progid.md) u otros atributos que impliquen a uno de ellos.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase** o miembro de **estructura**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Ejemplo

El código siguiente agrega una clave del registro denominada mi valor al sistema que describe el componente COM CMyClass.

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[registration_script](registration-script.md)
