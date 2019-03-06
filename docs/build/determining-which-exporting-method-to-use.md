---
title: Determinar el método de exportación que se debe utilizar
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 38006acfae90c3b216677684e9776f3ed5d7c1b1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422774"
---
# <a name="determining-which-exporting-method-to-use"></a>Determinar el método de exportación que se debe utilizar

Puede exportar las funciones de dos maneras: un archivo .def o `__declspec(dllexport)` palabra clave. Para ayudarle a decidir qué forma le resulta más adecuado para el archivo DLL, tenga en cuenta estas preguntas:

- ¿Va a exportar funciones más más adelante?

- ¿Es el archivo DLL utilizado únicamente por las aplicaciones que puede volver a generar o se utiliza por las aplicaciones que no se puede volver a generar, por ejemplo, las aplicaciones que se crean por parte de terceros?

## <a name="pros-and-cons-of-using-def-files"></a>Ventajas y desventajas del uso de archivos .def

Exportación de funciones en un archivo .def permite controlar los ordinales de exportación. Cuando se agrega una función exportada al archivo DLL, se puede asignar un valor ordinal mayor que cualquier otra función exportada. Al hacerlo, no es necesario volver a vincular con la biblioteca de importación que contiene la nueva función de las aplicaciones que utilizan la vinculación implícita. Esto resulta muy útil si está diseñando un archivo DLL para su uso por muchas aplicaciones ya que puede agregar nuevas funcionalidades y asegúrese también de que siguen funcionando correctamente con las aplicaciones que ya confían en ella. Por ejemplo, se crean los archivos DLL de MFC mediante archivos DEF.

Otra ventaja de utilizar un archivo .def es que puede usar el `NONAME` atributo para exportar una función. Esto coloca únicamente el ordinal en la tabla de exportaciones en el archivo DLL. Archivos DLL que tiene un gran número de funciones exportadas, mediante el `NONAME` atributo puede reducir el tamaño del archivo DLL. Para obtener información sobre cómo escribir una instrucción de definición de módulo, consulte [reglas para instrucciones de definición de módulo](../build/reference/rules-for-module-definition-statements.md). Para obtener información acerca de la exportación de ordinales, vea [exportar funciones desde un archivo DLL por Ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Una desventaja de utilizar un archivo .def es que, si va a exportar funciones en un archivo de C++, tiene que colocar los nombres representativos en el .def de archivos o define las funciones exportadas mediante el uso de extern "C" para evitar la decoración de nombres que ha realizado por el compilador de Visual C++.

Si coloca los nombres representativos en el archivo .def, se puede obtener mediante la [DUMPBIN](../build/reference/dumpbin-reference.md) herramienta o mediante el enlazador [/MAP](../build/reference/map-generate-mapfile.md) opción. Los nombres representativos producidos por el compilador son específicas del compilador; por lo tanto, si coloca los nombres representativos producidos por el compilador en un archivo .def, las aplicaciones que se vinculan al archivo DLL también deberán generarse mediante el uso de la misma versión del compilador para que los nombres representativos de la aplicación que realiza la llamada coincidan con los datos exportados nombres i n el archivo .def del archivo DLL.

## <a name="pros-and-cons-of-using-declspecdllexport"></a>Ventajas y desventajas del uso de __declspec (dllexport)

Uso de `__declspec(dllexport)` resulta útil porque no tiene que preocuparse por mantener un archivo .def y obtener los nombres representativos de las funciones exportadas. Sin embargo, la utilidad de este modo de exportación está limitada por el número de aplicaciones vinculadas que se están dispuesto a volver a generar. Si vuelve a generar el archivo DLL con nuevas exportaciones, también debe volver a generar las aplicaciones, ya que los nombres representativos para las funciones exportadas de C++ pueden cambiar si usa una versión diferente del compilador para volver a generarlo.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](../build/mutual-imports.md)

- [Nombres representativos](../build/reference/decorated-names.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)
