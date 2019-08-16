---
title: Source (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 79614a345e6c07b03df351da93a847fe12e4b110
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514025"
---
# <a name="source-c"></a>source (C++)

En una clase, especifica las interfaces de origen del objeto COM para los puntos de conexión. En una propiedad o un método, indica que el miembro devuelve un objeto o una variante que es un origen de eventos.

## <a name="syntax"></a>Sintaxis

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parámetros

*interfaces*<br/>
Una o más interfaces que se especifican al aplicar el atributo de origen a una clase. Este parámetro no se utiliza cuando el origen se aplica a una propiedad o un método.

## <a name="remarks"></a>Comentarios

El atributo de **origen** C++ tiene la misma funcionalidad que el atributo MIDL de [origen](/windows/win32/Midl/source) .

Puede usar el atributo [default](default-cpp.md) para especificar la interfaz de origen predeterminada de un objeto.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **estructura**, **interfaz**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|`coclass`(cuando se aplica a la clase o struct)|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[coclase](coclass.md)