---
title: módulo (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e999928e2080796c013107e3bc862d19426dbf88
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083533"
---
# <a name="module-c"></a>module (C++)

Define el bloque de biblioteca en el archivo .idl.

## <a name="syntax"></a>Sintaxis

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parámetros

*type*<br/>
(Opcional) Puede ser uno de los siguientes:

- `dll` Agrega funciones y clases que permiten la DLL resultante funcione como servidor COM en proceso. Este es el valor predeterminado.

- `exe` Agrega funciones y clases que permiten resultante funcione como un servidor fuera de proceso COM ejecutable.

- `service` Agrega funciones y clases que permiten resultante ejecutable funcione como un servicio NT.

- `unspecified` Deshabilita la inserción de código ATL relacionado con el atributo de módulo: la inserción de la clase de módulo de ATL, la instancia global _AtlModule y entrada de funciones de punto. No deshabilita la inserción de código ATL como consecuencia de otros atributos del proyecto.

*name*<br/>
(Opcional) El nombre del bloque de biblioteca.

*version*<br/>
(Opcional) El número de versión que desea asignar al bloque de biblioteca. El valor predeterminado es 1,0.

*uuid*<br/>
Identificador único para la biblioteca. Si omite este parámetro, se generará automáticamente un identificador para la biblioteca. Es posible que deba recuperar el *uuid* del bloque de biblioteca, lo que puede hacer con el identificador **__uuidof (** *nombrebiblioteca* **)**.

*lcid*<br/>
Parámetro de localización. Consulte [lcid](/windows/desktop/Midl/lcid) para obtener más información.

*control*<br/>
(Opcional) Especifica que todas las coclases de la biblioteca de controles.

*helpstring*<br/>
Especifica la biblioteca de tipos.

*helpstringdll*<br/>
(Opcional) Establece el nombre del archivo .dll se utiliza para realizar una búsqueda de cadena de documento. Consulte [helpstringdll](/windows/desktop/Midl/helpstringdll) para obtener más información.

*helpfile*<br/>
(Opcional) El nombre de la **ayuda** archivo para la biblioteca de tipos.

*helpcontext*<br/>
(Opcional) El **Id. de Ayuda** para esta biblioteca de tipos.

*helpstringcontext*<br/>
(Opcional) Consulte [helpstringcontext](helpstringcontext.md) para obtener más información.

*hidden*<br/>
(Opcional) Impide que aparezca toda la biblioteca. Este uso está diseñado para emplearlo con controles. Los hosts deben crear una biblioteca de tipos que ajuste el control con propiedades extendidas. Consulte el atributo MIDL [hidden](/windows/desktop/Midl/hidden) para obtener más información.

*restricted*<br/>
(Opcional) Los miembros de la biblioteca no se puede llamar arbitrariamente. Consulte el atributo MIDL [restricted](/windows/desktop/Midl/restricted) para obtener más información.

*custom*<br/>
(Opcional) Uno o más atributos; Esto es similar a la [personalizado](custom-cpp.md) atributo. El primer parámetro *personalizado* es el GUID del atributo. Por ejemplo:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Identificador de recurso de cadena del archivo .rgs usado para registrar el identificador de aplicación de la DLL, el ejecutable o el servicio. Cuando el módulo es de tipo service, este argumento también se usa para obtener el identificador de la cadena que contiene el nombre del servicio.

> [!NOTE]
> Tanto el archivo .rgs como la cadena que contiene el nombre del servicio deben contener el mismo valor numérico.

## <a name="remarks"></a>Comentarios

A menos que especifique el parámetro *restricted* en [emitidl](emitidl.md), se requiere **module** en todos los programas que usen atributos de C++.

Se creará un bloque de biblioteca si, además del atributo **module** , el código fuente también usa [dispinterface](dispinterface.md), [dual](dual.md), [object](object-cpp.md)o un atributo que implique [coclase](coclass.md).

Se permite un bloque de biblioteca en un archivo .idl. Si en el código fuente hay varias entradas de módulo, se combinarán con los valores de parámetro más recientes que se implementen.

Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento anterior, el atributo también inserta un objeto global (denominado `_AtlModule`) del tipo correcto y el código de soporte técnico adicionales. Si el atributo es independiente, inserta una clase derivada del tipo de módulo correcto. Si el atributo se aplica a una clase, agrega una clase base del tipo de módulo correcto. El tipo correcto viene determinada por el valor de la *tipo* parámetro:

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) se usa como clase base y como los puntos de entrada del archivo DLL estándar necesarios para un servidor COM. Estos puntos de entrada son [DllMain](/windows/desktop/Dlls/dllmain), [DllRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)y [DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) se usa como clase base y como el punto de entrada ejecutable estándar [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Biblioteca de](/windows/desktop/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)  