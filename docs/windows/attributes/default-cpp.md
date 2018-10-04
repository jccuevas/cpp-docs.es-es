---
title: predeterminado (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fb7f205ccdf78e1ef64e2ba2c132e3c2b6b6000
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792479"
---
# <a name="default-c"></a>default (C++)

Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.

## <a name="syntax"></a>Sintaxis

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parámetros

*interface1*<br/>
Interfaz predeterminada que estará disponible para los entornos de scripting que crean un objeto basado en la clase definida con el atributo **default** .

Si no se especifica ninguna interfaz predeterminada, se usa la primera aparición de una interfaz sin origen como valor predeterminado.

*Interfaz2*<br/>
(Opcional) La interfaz de origen predeterminada. También debe especificar esta interfaz con el [origen](source-cpp.md) atributo.

Si no se especifica ninguna interfaz de origen predeterminada, se usa la primera interfaz de origen como valor predeterminado.

## <a name="remarks"></a>Comentarios

El **predeterminada** atributo de C++ tiene la misma funcionalidad que el [predeterminada](/windows/desktop/Midl/default) atributo MIDL. El **predeterminada** atributo también se usa con el [caso](case-cpp.md) atributo.

## <a name="example"></a>Ejemplo

El siguiente código muestra cómo **predeterminada** se utiliza en la definición de una coclase especificar `ICustomDispatch` como la interfaz de programación predeterminada:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

El [origen](source-cpp.md) atributo también tiene un ejemplo de cómo usar **predeterminada**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**, miembro de datos|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a **clase** o **struct**)|
|**Atributos no válidos**|Ninguna|

Para obtener más información, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[coclass](coclass.md)  