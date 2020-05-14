---
title: Determinación del método de exportación que se va a usar
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273742"
---
# <a name="determine-which-exporting-method-to-use"></a>Determinación del método de exportación que se va a usar

Hay dos maneras de exportar funciones: con un archivo .def o la palabra clave `__declspec(dllexport)`. Para ayudarle a decidir cuál es mejor para el archivo DLL, tenga en cuenta estas preguntas:

- ¿Tiene pensado exportar más funciones en el futuro?

- ¿El archivo DLL solo se usa en aplicaciones que se pueden recompilar, o bien en aplicaciones que no se pueden recompilar (por ejemplo, aplicaciones creadas por terceros)?

## <a name="pros-and-cons-of-using-def-files"></a>Ventajas y desventajas de usar archivos .def

La exportación de funciones en un archivo .def proporciona el control sobre los ordinales de exportación. Cuando se agrega una función exportada al archivo DLL, se le puede asignar un valor ordinal mayor que cualquier otra función exportada. Al hacerlo, las aplicaciones que usan la vinculación implícita no se tienen que volver a vincular con la biblioteca de importación que contiene la nueva función. Esto resulta muy práctico si va a diseñar un archivo DLL para que lo usen muchas aplicaciones, ya que puede agregar funciones nuevas y también asegurarse de que sigue funcionando correctamente con las aplicaciones que ya se basan en él. Por ejemplo, los archivos DLL de MFC se compilan mediante archivos .def.

Otra ventaja de usar un archivo .def es que puede utilizar el atributo `NONAME` para exportar una función. Esto coloca solo el ordinal en la tabla de exportaciones del archivo DLL. Para los archivos DLL con un gran número de funciones exportadas, el uso del atributo `NONAME` puede reducir el tamaño del archivo DLL. Para obtener información sobre cómo escribir una instrucción de definición de módulos, vea [Reglas para instrucciones de definición de módulos](reference/rules-for-module-definition-statements.md). Para obtener información sobre la exportación de ordinales, vea [Exportación de funciones desde un archivo DLL por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Una desventaja de usar un archivo .def es que si va a exportar funciones en un archivo de C++, tendrá que colocar los nombres representativos en el archivo .def o definir las funciones exportadas mediante extern "C" para evitar la decoración de nombres que realiza el compilador de MSVC.

Si coloca los nombres representativos en el archivo .def, puede obtenerlos mediante la herramienta [DUMPBIN](reference/dumpbin-reference.md) o la opción del enlazador [/MAP](reference/map-generate-mapfile.md). Los nombres representativos que genera el compilador son específicos de él; por tanto, si los coloca en un archivo .def, las aplicaciones que se vinculan al archivo DLL también se deben compilar con la misma versión del compilador para que los nombres representativos de la aplicación que realiza la llamada coincidan con los nombres exportados del archivo . def de la DLL.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>Ventajas y desventajas de usar __declspec(dllexport)

El uso de `__declspec(dllexport)` es conveniente porque no tiene que preocuparse de mantener un archivo .def ni de obtener los nombres representativos de las funciones exportadas. Pero la utilidad de este tipo de exportación está limitada por el número de aplicaciones vinculadas que esté dispuesto a recompilar. Si vuelve a generar el archivo DLL con nuevas exportaciones, también tiene que recompilar las aplicaciones porque es posible que los nombres representativos de las funciones de C++ exportadas cambien si usa otra versión del compilador para recompilarlo.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL mediante archivos .DEF](exporting-from-a-dll-using-def-files.md)

- [Exportación desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportación de funciones de C para usarlas en ejecutables del lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicialización de un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

- [Nombres representativos](reference/decorated-names.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
