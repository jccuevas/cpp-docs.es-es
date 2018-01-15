---
title: "módulo (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.module
dev_langs: C++
helpviewer_keywords: module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75b41ea146096a60210918b5f21e7b6278e35001
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="module-c"></a>module (C++)
Define el bloque de biblioteca en el archivo .idl.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ module (  
   type=dll,  
   name=string,  
   version=1.0,  
   uuid=uuid,  
   lcid=integer,  
   control=boolean,  
   helpstring=string,  
   helpstringdll=string,  
   helpfile=string,  
   helpcontext=integer,  
   helpstringcontext=integer,  
   hidden=boolean,  
   restricted=boolean,  
   custom=string,  
   resource_name=string,  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 ***type***  (opcional)  
 Puede ser uno de los siguientes:  
  
-   **dll** Agrega funciones y clases que permiten que la DLL resultante funcione como servidor COM en proceso. Este es el valor predeterminado.  
  
-   **exe** Agrega funciones y clases que permiten que el ejecutable resultante funcione como servidor COM fuera de proceso.  
  
-   **service** Agrega funciones y clases que permiten que el ejecutable resultante funcione como servicio NT.  
  
-   **unspecified** Deshabilita la inserción de código ATL relacionado con el atributo de módulo: la inserción de la clase de módulo de ATL, la instancia global _AtlModule y funciones de punto de entrada.  No deshabilita la inserción de código ATL como consecuencia de otros atributos del proyecto.  
  
 ***name***  (opcional)  
 Nombre del bloque de biblioteca.  
  
 ***version***  (opcional)  
 Número de versión que quiere asignar al bloque de biblioteca. El valor predeterminado es 1,0.  
  
 `uuid`  
 Identificador único para la biblioteca. Si omite este parámetro, se generará automáticamente un identificador para la biblioteca. Es posible que necesite recuperar el *uuid* del bloque de biblioteca, lo que puede hacer con el identificador **__uuidof (***nombreDeBiblioteca***)**.  
  
 **lcid**  
 Parámetro de localización. Consulte [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) para obtener más información.  
  
 **control** (opcional)  
 Especifica que todas las coclases de la biblioteca son controles.  
  
 **helpstring**  
 Especifica la biblioteca de tipos.  
  
 ***helpstringdll***  (opcional)  
 Establece el nombre del archivo .dll que se va a usar para realizar una búsqueda de cadenas del documento. Consulte [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) para obtener más información.  
  
 **helpfile** (opcional)  
 Nombre del archivo de ayuda para la biblioteca de tipos.  
  
 **helpcontext** (opcional)  
 Identificador de ayuda para esta biblioteca de tipos.  
  
 **helpstringcontext** (opcional)  
 Consulte [helpstringcontext](../windows/helpstringcontext.md) para obtener más información.  
  
 **hidden** (opcional)  
 Impide que se muestre toda la biblioteca. Este uso está diseñado para emplearlo con controles. Los hosts deben crear una biblioteca de tipos que ajuste el control con propiedades extendidas. Consulte el atributo MIDL [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) para obtener más información.  
  
 **restricted** (opcional)  
 No es posible llamar a los miembros de la biblioteca arbitrariamente. Consulte el atributo MIDL [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) para obtener más información.  
  
 ***custom***  (opcional)  
 Uno o más atributos; esto es similar al atributo [custom](../windows/custom-cpp.md) . El primer parámetro de `custom` es el GUID del atributo. Por ejemplo:  
  
```  
[module(custom={guid,1}, custom={guid1,2})]  
```  
  
 **resource_name**  
 Identificador de recurso de cadena del archivo .rgs usado para registrar el identificador de aplicación de la DLL, el ejecutable o el servicio. Cuando el módulo es de tipo service, este argumento también se usa para obtener el identificador de la cadena que contiene el nombre del servicio.  
  
> [!NOTE]
>  Tanto el archivo .rgs como la cadena que contiene el nombre del servicio deben contener el mismo valor numérico.  
  
## <a name="remarks"></a>Comentarios  
 A menos que especifique el parámetro **restricted** en [emitidl](../windows/emitidl.md), se requiere **module** en todos los programas que usen atributos de C++.  
  
 Se creará un bloque de biblioteca si, además del atributo **module** , el código fuente también usa [dispinterface](../windows/dispinterface.md), [dual](../windows/dual.md), [object](../windows/object-cpp.md)o un atributo que implique [coclase](../windows/coclass.md).  
  
 Se permite un bloque de biblioteca en un archivo .idl. Si en el código fuente hay varias entradas de módulo, se combinarán con los valores de parámetro más recientes que se implementen.  
  
 Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento anterior, el atributo también inserta un objeto global (denominado **_AtlModule**) del tipo correcto y el código de soporte adicional. Si el atributo es independiente, inserta una clase derivada del tipo de módulo correcto. Si el atributo se aplica a una clase, agrega una clase base del tipo de módulo correcto. El tipo correcto lo determina el valor del parámetro `type` :  
  
-   `type` = **dll**  
  
     [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) se usa como clase base y como los puntos de entrada del archivo DLL estándar necesarios para un servidor COM. Estos puntos de entrada son [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583), [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368)y [DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891).  
  
-   `type` = **exe**  
  
     [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **service**  
  
     [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **unspecified**  
  
     Deshabilita la inserción de código ATL relacionado con el atributo de módulo.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo crear un bloque de biblioteca en el archivo .idl generado.  
  
```  
// cpp_attr_ref_module1.cpp  
// compile with: /LD  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
```  
  
 En el código siguiente se muestra que puede proporcionar su propia implementación de una función que aparecerá en el código insertado como resultado de usar **module**. Consulte [/Fx](../build/reference/fx-merge-injected-code.md) para obtener más información sobre cómo ver código insertado. Para reemplazar una de las funciones insertadas por el atributo **module** , cree una clase que contendrá la implementación de la función y haga que el atributo **module** se aplique a esa clase.  
  
```  
// cpp_attr_ref_module2.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// no semicolon after attribute block  
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [usesgetlasterror](../windows/usesgetlasterror.md)   
 [biblioteca de](http://msdn.microsoft.com/library/windows/desktop/aa367069)   
 [HelpContext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
 [HelpFile](../windows/helpfile.md)   
 [version](../windows/version-cpp.md)   
