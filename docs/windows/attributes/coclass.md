---
title: coclass (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 76540e90fef2e840b91bb07f570a7b8c0987eb10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168336"
---
# <a name="coclass"></a>coclase

Crea un objeto COM, que puede implementar una interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
[coclass]
```

## <a name="remarks"></a>Observaciones

El atributo **CoClass** C++ coloca una construcción de coclase en el archivo. idl generado.

Al definir una coclase, también puede especificar los atributos [UUID](uuid-cpp-attributes.md), [version](version-cpp.md), [Threading](threading-cpp.md), [vi_progid](vi-progid.md)y [ProgID](progid.md) . Si no se especifica ninguno de ellos, se generará.

Si dos archivos de encabezado contienen clases con el atributo **CoClass** y no especifican un GUID, el compilador utilizará el mismo GUID para ambas clases y se producirá un error de MIDL.  Por lo tanto, debe usar el atributo `uuid` al usar **CoClass**.

**Proyectos ATL**

Cuando este atributo precede a una definición de clase o estructura en un proyecto ATL, se:

- Inserta código o datos para admitir el registro automático del objeto.

- Inserta código o datos para admitir un generador de clases COM para el objeto.

- Inserta código o datos para implementar `IUnknown` y convertir el objeto en un objeto que se pueda crear COM.

En concreto, las siguientes clases base se agregan al objeto de destino:

- [CComCoClass (clase](../../atl/reference/ccomcoclass-class.md) ) proporciona el generador de clases predeterminado y el modelo de agregación para el objeto.

- [CComObjectRootEx (clase](../../atl/reference/ccomobjectrootex-class.md) ) tiene una plantilla basada en la clase de modelo de subprocesos especificada por el atributo [Threading](threading-cpp.md) . Si no se especifica el atributo `threading`, el modelo de subprocesos predeterminado es Apartment.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) se agrega si no se especifica el atributo [noncreatable](noncreatable.md) para el objeto de destino.

Por último, cualquier interfaz dual que no se haya definido mediante IDL incrustado se reemplaza por la clase [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) correspondiente. Si la interfaz dual se define en IDL incrustado, la interfaz concreta de la lista base no se modifica.

El atributo **CoClass** también hace que las siguientes funciones estén disponibles a través del código insertado o, en el caso de `GetObjectCLSID`, como un método estático en la clase base `CComCoClass`:

- `UpdateRegistry` registra los generadores de clase de la clase de destino.

- `GetObjectCLSID`, que está relacionado con el registro, también se puede usar para obtener el CLSID de la clase de destino.

- de forma predeterminada `GetObjectFriendlyName` devuelve una cadena con el formato "\<*nombre de clase de destino*> `Object`". Si esta función ya está presente, no se agrega. Agregue esta función a la clase de destino para devolver un nombre más descriptivo que el generado automáticamente.

- `GetProgID`, que está relacionado con el registro, devuelve la cadena especificada con el atributo [ProgID](progid.md) .

- `GetVersionIndependentProgID` tiene la misma funcionalidad que `GetProgID`, pero devuelve la cadena especificada con [vi_progid](vi-progid.md).

Los cambios siguientes, que están relacionados con el mapa COM, se realizan en la clase de destino:

- Se agrega un mapa COM con entradas para todas las interfaces de las que se deriva la clase de destino y todas las entradas especificadas por el atributo de puntos de entrada de la [interfaz com](../../mfc/com-interface-entry-points.md) o las que requiere el atributo de [agregados](aggregates.md) .

- Se inserta una macro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) en el mapa com.

El nombre de la coclase generada en el archivo. idl para la clase tendrá el mismo nombre que la clase.  Por ejemplo, y al hacer referencia al ejemplo siguiente, para tener acceso al identificador de clase de una coclase `CMyClass`, en un cliente a través del archivo de encabezado generado por MIDL, utilice `CLSID_CMyClass`.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar el atributo **CoClass** :

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

En el ejemplo siguiente se muestra cómo invalidar la implementación predeterminada de una función que aparece en el código inyectado por el atributo **CoClass** . Consulte [/Fx](../../build/reference/fx-merge-injected-code.md) para obtener más información sobre cómo ver código insertado. Las clases base o las interfaces que use para una clase aparecerán en el código insertado. Además, si una clase se incluye de forma predeterminada en el código insertado y se especifica explícitamente esa clase como base para su coclase, el proveedor de atributos usará el formulario especificado en el código.

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
