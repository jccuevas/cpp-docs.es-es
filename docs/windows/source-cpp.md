---
title: origen (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ccd5f5220a49ddb63554b4c3b96533a3066d4d4b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214598"
---
# <a name="source-c"></a>source (C++)

En una clase, especifica las interfaces de origen del objeto COM para puntos de conexión. En una propiedad o método, indica que el miembro devuelve un objeto o una variante de un origen de eventos.

## <a name="syntax"></a>Sintaxis

```cpp
[ source(
   interfaces
) ]
```

### <a name="parameters"></a>Parámetros

*interfaces*  
Una o más interfaces que especifique cuando se aplica el origen de atributo a una clase. Este parámetro no se utiliza cuando el origen se aplica a una propiedad o método.

## <a name="remarks"></a>Comentarios

El **origen** atributo de C++ tiene la misma funcionalidad que el [origen](/windows/desktop/Midl/source) atributo MIDL.

Puede usar el [predeterminada](../windows/default-cpp.md) atributo para especificar la interfaz de origen predeterminada para un objeto.

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
|**Se aplica a**|**clase**, **struct**, **interfaz**|
|**Reiterativo**|No|
|**Atributos requeridos**|`coclass` (cuando se aplica a la clase o struct)|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de clase](../windows/class-attributes.md)  
[Atributos de método](../windows/method-attributes.md)  
[coclass](../windows/coclass.md)  