---
title: "coclass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.coclass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "coclass attribute"
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# coclass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

crea un objeto COM, que puede implementar una interfaz COM.  
  
## Sintaxis  
  
```  
  
[coclass]  
  
```  
  
## Comentarios  
 El atributo de **CoClass** C\+\+ coloca una construcción coclass en el archivo generado .idl.  
  
 Al definir una coclase, también puede especificar [uuid](../windows/uuid-cpp-attributes.md), [versión](../windows/version-cpp.md), [subprocesamiento](../windows/threading-cpp.md), [vi\_progid](../windows/vi-progid.md), y los atributos de [ProgID](../Topic/progid.md) .  Si ninguno de ellos no se especifica, se generará.  
  
 Si dos archivos de encabezado contienen clases con el atributo de **CoClass** y no especifican GUID, el compilador utilizará mismo GUID para las dos clases, y se producirán un error MIDL.  Por consiguiente, debe usar el atributo de `uuid` cuando se utiliza **CoClass**.  
  
 **Proyectos de ATL**  
  
 Cuando este atributo precede a una definición de clase o estructura en un proyecto ATL, él:  
  
-   Inserta código o datos para admitir el registro automático para el objeto.  
  
-   Inserta código o datos para admitir un generador de clases COM para el objeto.  
  
-   Inserta código o datos para implementar **IUnknown** y crear el objeto un objeto de COM\-creatable.  
  
 Específicamente, las clases base siguientes se agregan al objeto de destino:  
  
-   [clase de CComCoClass](../atl/reference/ccomcoclass-class.md) proporciona el modelo predeterminado de generador y la agregación de clase del objeto.  
  
-   [clase de CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) tiene una plantilla basada en la clase del modelo de subprocesos especificada por el atributo de [subprocesamiento](../windows/threading-cpp.md) .  si el atributo de **subprocesamiento** no se especifica, el modelo de subprocesos predeterminado es apartamento.  
  
-   Se agrega[IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) si el atributo de [noncreatable](../windows/noncreatable.md) no se especifica para el objeto de destino.  
  
 Finalmente, cualquier interfaz dual que no está definido mediante IDL incrustado se reemplaza con la clase correspondiente de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) .  Si la interfaz dual está definido en IDL incrustado, la interfaz determinada en la lista base no se modifica.  
  
 El atributo de **CoClass** también crea las siguientes funciones disponible mediante código insertado, o en el caso de `GetObjectCLSID`, como un método estático en la clase base `CComCoClass`:  
  
-   `UpdateRegistry` registra los generadores de clases de la clase de destino.  
  
-   `GetObjectCLSID`, relacionado con el registro, también se puede utilizar para obtener el CLSID de la clase de destino.  
  
-   **GetObjectFriendlyName** de forma predeterminada devuelve una cadena de formato “*name\>*`Object`*de la clase*de \<target”.  Si esta función ya está presente, no se agrega.  Agregue esta función a la clase de destino para devolver un nombre más descriptivo que el generado automáticamente.  
  
-   **GetProgID**, relacionado con el registro, devuelve la cadena especificada con el atributo de [ProgID](../Topic/progid.md) .  
  
-   **GetVersionIndependentProgID** tiene la misma funcionalidad que **GetProgID**, pero devuelve la cadena especificada con [vi\_progid](../windows/vi-progid.md).  
  
 Los cambios siguientes, que se relacionan con el mapa COM, se realizan en la clase de destino:  
  
-   Un mapa COM se agrega con las entradas para todas las interfaces que la clase de destino se deriva de y todas las entradas especificado por el atributo de [Puntos de entrada de interfaz COM](../mfc/com-interface-entry-points.md) o las necesarias en el atributo de [agregados](../windows/aggregates.md) .  
  
-   Una macro de [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md) se inserta en el mapa COM.  Esta macro es similar a [OBJECT\_ENTRY](http://msdn.microsoft.com/es-es/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) en términos de funcionalidad pero no necesita ser parte del mapa COM de la clase de destino.  
  
 El nombre de la coclase generados en el archivo .idl para la clase tendrá el mismo nombre que la clase.  Por ejemplo, y haciendo referencia al ejemplo siguiente, para tener acceso al identificador de la clase para coclase CMyClass, en un cliente en el archivo de encabezado generado por MIDL, utilice CLSID\_CMyClass.  
  
## Ejemplo  
 el código siguiente muestra cómo utilizar el atributo de **CoClass** :  
  
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
  
 El ejemplo siguiente muestra cómo invalidar la implementación predeterminada de una función que aparece en el código insertado por el atributo de **CoClass** .  Vea [\/Fx](../build/reference/fx-merge-injected-code.md) para obtener más información sobre código insertado de la vista.  Las clases base o interfaz que se utilice para una clase se aparecen en el código insertado.   Además, si una clase está incluido de forma predeterminada en el código insertado y se especifica explícitamente esa clase como base para la coclase, el proveedor de atributo utilizará el formato especificado en el código.  
  
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
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../Topic/appobject.md)