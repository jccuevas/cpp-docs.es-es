---
title: coclase | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5eb9c7e632151c039b76a0f389cd18c68c0740ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33867017"
---
# <a name="coclass"></a>coclase
Crea un objeto COM, que puede implementar una interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[coclass]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **coclase** atributo C++ coloca una construcción de coclase en el archivo .idl generado.  
  
 Al definir una coclase, también puede especificar el [uuid](../windows/uuid-cpp-attributes.md), [versión](../windows/version-cpp.md), [subprocesamiento](../windows/threading-cpp.md), [vi_progid](../windows/vi-progid.md), y [progid ](../windows/progid.md) atributos. Si alguno de ellos no se especifica, se generará.  
  
 Si dos archivos de encabezado contienen clases con el **coclase** de atributo y no se especifica un GUID, el compilador usa el mismo GUID para ambas clases y que producirán un error de MIDL.  Por lo tanto, debe utilizar el `uuid` cuando se usa el atributo **coclase**.  
  
 **Proyectos ATL**  
  
 Cuando este atributo precede a una definición de clase o estructura en un proyecto ATL,:  
  
-   Inserta código o datos para admitir el registro automático para el objeto.  
  
-   Inserta código o datos para admitir un generador de clases COM para el objeto.  
  
-   Inserta código o datos que se va a implementar **IUnknown** y hacer que un objeto COM que se puede crear el objeto.  
  
 En concreto, las clases base siguientes se agregan al objeto de destino:  
  
-   [Clase CComCoClass](../atl/reference/ccomcoclass-class.md) proporciona el modelo de generador y agregación de clase predeterminado para el objeto.  
  
-   [Clase CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) tiene una plantilla basada en la clase de modelo de subprocesamiento especificada por el [subprocesamiento](../windows/threading-cpp.md) atributo. Si el **subprocesamiento** atributo no se especifica, el valor predeterminado modelo de subprocesos es un contenedor.  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) se agrega si el [noncreatable](../windows/noncreatable.md) no se especifica el atributo para el objeto de destino.  
  
 Por último, se reemplaza cualquier interfaz dual que no se define mediante IDL incrustado con la correspondiente [IDispatchImpl](../atl/reference/idispatchimpl-class.md) clase. Si se define la interfaz dual en IDL incrustado, no se modifica la interfaz concreta en la lista base.  
  
 El **coclase** atributo también hace las siguientes funciones estén disponibles a través de código insertado, o en el caso de `GetObjectCLSID`, como un método estático en la clase base `CComCoClass`:  
  
-   `UpdateRegistry` registra los generadores de clases de la clase de destino.  
  
-   `GetObjectCLSID`, que está relacionada con el registro, también puede utilizarse para obtener el CLSID de la clase de destino.  
  
-   **GetObjectFriendlyName** de forma predeterminada, devuelve una cadena con el formato "\<*nombre de la clase de destino*> `Object`". Si esta función está presente, no se agrega. Agregue esta función a la clase de destino para devolver un nombre más descriptivo que se generó automáticamente.  
  
-   **GetProgID**, que está relacionada con el registro, que devuelve la cadena especificada con el [progid](../windows/progid.md) atributo.  
  
-   **GetVersionIndependentProgID** tiene la misma funcionalidad que **GetProgID**, pero devuelve la cadena especificada con [vi_progid](../windows/vi-progid.md).  
  
 Los cambios siguientes, que están relacionadas con la asignación COM, se realizan en la clase de destino:  
  
-   Se agrega una asignación de COM con entradas para todas las interfaces que se deriva la clase de destino y todas las entradas especificadas por el [puntos de entrada de la interfaz COM](../mfc/com-interface-entry-points.md) atributo o las que necesitan la [agregados](../windows/aggregates.md) atributo.  
  
-   Un [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto) macro se inserta en el mapa COM.
  
 El nombre de la coclase generado en el archivo .idl para la clase tendrán el mismo nombre que la clase.  Por ejemplo, que hace referencia al siguiente ejemplo, para tener acceso a lo Id. de clase de una coclase CMyClass, en un cliente a través del archivo de encabezado generados por MIDL, utilice CLSID_CMyClass.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el **coclase** atributo:  
  
```  
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
  
 El ejemplo siguiente muestra cómo invalidar la implementación predeterminada de una función que aparece en el código insertado por el **coclase** atributo. Consulte [/Fx](../build/reference/fx-merge-injected-code.md) para obtener más información sobre cómo ver código insertado. Las interfaces que usan para una clase o clases base se aparecerá en el código insertado.   Además, si una clase se incluye de forma predeterminada en el código insertado y especificar explícitamente esa clase como base para la coclase, el proveedor de atributo usará el formato especificado en el código.  
  
```  
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
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos COM](../windows/com-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)