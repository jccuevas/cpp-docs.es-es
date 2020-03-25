---
title: Module (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: e93073a1728063038ddd4e28dbb313854ee3c8c5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166697"
---
# <a name="module-c"></a>module (C++)

Define el bloque de biblioteca en el archivo .idl.

## <a name="syntax"></a>Sintaxis

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parámetros

*type*<br/>
Opta Puede ser uno de los siguientes:

- `dll` agrega funciones y clases que permiten que la DLL resultante funcione como servidor COM en proceso. Este es el valor predeterminado.

- `exe` agrega funciones y clases que permiten que el ejecutable resultante funcione como servidor COM fuera de proceso.

- `service` agrega funciones y clases que permiten que el ejecutable resultante funcione como un servicio NT.

- `unspecified` deshabilita la inserción de código ATL relacionado con el atributo de módulo: la inserción de la clase de módulo ATL, el _AtlModule de instancia global y las funciones de punto de entrada. No deshabilita la inserción de código ATL como consecuencia de otros atributos del proyecto.

*name*<br/>
Opta Nombre del bloque de biblioteca.

*version*<br/>
Opta El número de versión que desea asignar al bloque de biblioteca. El valor predeterminado es 1.0.

*uuid*<br/>
Identificador único para la biblioteca. Si omite este parámetro, se generará automáticamente un identificador para la biblioteca. Es posible que necesite recuperar el *UUID* del bloque de biblioteca, lo que puede hacer mediante el identificador **__uuidof (** *nombrebiblioteca* **)** .

*lcid*<br/>
Parámetro de localización. Consulte [lcid](/windows/win32/Midl/lcid) para obtener más información.

*control*<br/>
Opta Especifica que todas las coclases de la biblioteca son controles.

*helpstring*<br/>
Especifica la biblioteca de tipos.

*helpstringdll*<br/>
Opta Establece el nombre del archivo. dll que se va a usar para realizar una búsqueda de cadena de documento. Consulte [helpstringdll](/windows/win32/Midl/helpstringdll) para obtener más información.

*helpfile*<br/>
Opta Nombre del archivo de **ayuda** para la biblioteca de tipos.

*helpcontext*<br/>
Opta El **identificador** de la ayuda para esta biblioteca de tipos.

*helpstringcontext*<br/>
Opta Vea [helpstringcontext](helpstringcontext.md) para obtener más información.

*hidden*<br/>
Opta Impide que se muestre toda la biblioteca. Este uso está diseñado para emplearlo con controles. Los hosts deben crear una biblioteca de tipos que ajuste el control con propiedades extendidas. Consulte el atributo MIDL [hidden](/windows/win32/Midl/hidden) para obtener más información.

*restricted*<br/>
Opta No se puede llamar a los miembros de la biblioteca arbitrariamente. Consulte el atributo MIDL [restricted](/windows/win32/Midl/restricted) para obtener más información.

*custom*<br/>
Opta Uno o más atributos; Esto es similar al atributo [personalizado](custom-cpp.md) . El primer parámetro de *Custom* es el GUID del atributo. Por ejemplo:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Identificador de recurso de cadena del archivo .rgs usado para registrar el identificador de aplicación de la DLL, el ejecutable o el servicio. Cuando el módulo es de tipo service, este argumento también se usa para obtener el identificador de la cadena que contiene el nombre del servicio.

> [!NOTE]
> Tanto el archivo .rgs como la cadena que contiene el nombre del servicio deben contener el mismo valor numérico.

## <a name="remarks"></a>Observaciones

A menos que especifique el parámetro *restricted* en [emitidl](emitidl.md), se requiere **module** en todos los programas que usen atributos de C++.

Se creará un bloque de biblioteca si, además del atributo **module** , el código fuente también usa [dispinterface](dispinterface.md), [dual](dual.md), [object](object-cpp.md)o un atributo que implique [coclase](coclass.md).

Se permite un bloque de biblioteca en un archivo .idl. Si en el código fuente hay varias entradas de módulo, se combinarán con los valores de parámetro más recientes que se implementen.

Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento anterior, el atributo también inserta un objeto global (denominado `_AtlModule`) del tipo correcto y el código de soporte adicional. Si el atributo es independiente, inserta una clase derivada del tipo de módulo correcto. Si el atributo se aplica a una clase, agrega una clase base del tipo de módulo correcto. El tipo correcto viene determinado por el valor del parámetro de *tipo* :

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) se usa como clase base y como los puntos de entrada del archivo DLL estándar necesarios para un servidor COM. Estos puntos de entrada son [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)y [DllGetClassObject](/previous-versions//dd797891\(v=vs.85\)).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **unspecified**

   Deshabilita la inserción de código ATL relacionado con el atributo de módulo.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo crear un bloque de biblioteca en el archivo .idl generado.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

En el código siguiente se muestra que puede proporcionar su propia implementación de una función que aparecerá en el código insertado como resultado de usar **module**. Consulte [/Fx](../../build/reference/fx-merge-injected-code.md) para obtener más información sobre cómo ver código insertado. Para reemplazar una de las funciones insertadas por el atributo **module** , cree una clase que contendrá la implementación de la función y haga que el atributo **module** se aplique a esa clase.

```cpp
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
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Biblioteca](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)
