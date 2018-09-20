---
title: dual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dual
dev_langs:
- C++
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6af52fab983f93964ba33cf59ca38783df66b5da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373586"
---
# <a name="dual"></a>dual

Coloca una interfaz en el archivo .idl como una interfaz dual.

## <a name="syntax"></a>Sintaxis

```cpp
[dual]
```

## <a name="remarks"></a>Comentarios

Cuando el **dual** atributo de C++ precede a una interfaz, hace que la interfaz colocarse dentro del bloque de biblioteca en el archivo .idl generado.

## <a name="example"></a>Ejemplo

El código siguiente es un bloque de atributos que usa **dual** antes de una definición de interfaz:

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([in] long nSize); 
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dispinterface`|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos por uso](../windows/attributes-by-usage.md)<br/>
[Personalizado](../windows/custom-cpp.md)<br/>
[dispinterface](../windows/dispinterface.md)<br/>
[object](../windows/object-cpp.md)<br/>
[__interface](../cpp/interface.md)  