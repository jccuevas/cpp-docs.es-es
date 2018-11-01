---
title: Exportar desde un archivo DLL mediante archivos DEF
ms.date: 11/04/2016
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: e4351d8eca6c6c580430aa8988344bf7f57e0a9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553912"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportar desde un archivo DLL mediante archivos DEF

Un archivo de definición de módulo (.def) es un archivo de texto que contiene una o varias instrucciones de módulo que describen distintos atributos de un archivo DLL. Si no usa el **__declspec (dllexport)** palabra clave para exportar las funciones de DLL, el archivo DLL requerirá un archivo .def.

Un archivo .def mínimo debe contener las siguientes instrucciones de definición de módulo:

- La primera instrucción en el archivo debe ser la instrucción LIBRARY. Esta instrucción identifica el archivo .def como perteneciente a un archivo DLL. La instrucción LIBRARY está seguida del nombre del archivo DLL. El vinculador coloca este nombre en la biblioteca de importación del archivo DLL.

- La instrucción EXPORTS muestra los nombres y, opcionalmente, los valores ordinales de las funciones exportadas por el archivo DLL. Asignar un valor ordinal de la función con nombre de la función con una arroba (@) y un número. Cuando especifique valores ordinales, deben estar en el intervalo de 1 a N, donde N es el número de funciones exportadas por el archivo DLL. Si desea exportar funciones por ordinal, vea [exportar funciones desde un archivo DLL por Ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) , así como en este tema.

Por ejemplo, un archivo DLL que contiene el código para implementar un árbol de búsqueda binaria podría ser similar al siguiente:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Si usas el [Asistente para archivos DLL de MFC](../mfc/reference/mfc-dll-wizard.md) para crear una DLL de MFC, el asistente crea un archivo .def esqueleto y lo agrega automáticamente al proyecto. Agregue los nombres de las funciones que se exportarán a este archivo. Para que no son archivos DLL en MFC, debe crear usted mismo el archivo .def y agregarlo al proyecto.

Si va a exportar funciones en un archivo de C++, tendrá que colocar los nombres representativos en el archivo .def o definir las funciones exportadas con vinculación C estándar utilizando extern "C". Si tiene que colocar los nombres representativos en el archivo .def, se puede obtener mediante la [DUMPBIN](../build/reference/dumpbin-reference.md) herramienta o mediante el enlazador [/MAP](../build/reference/map-generate-mapfile.md) opción. Tenga en cuenta que los nombres representativos producidos por el compilador serán específicos del compilador. Si coloca los nombres representativos producidos por el compilador de Visual C++ en un archivo .def, las aplicaciones que estén vinculadas al archivo DLL deben compilarse también utilizan la misma versión de Visual C++ para que los nombres representativos de la aplicación que realiza la llamada coincidan con los nombres exportados .de del archivo DLL archivo f.

Si está creando un [archivo DLL de extensión](../build/extension-dlls-overview.md), y exportando mediante un archivo .def, coloque el código siguiente al principio y al final de los archivos de encabezado que contienen las clases exportadas:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Estas líneas garantizan que las variables MFC utilizadas internamente o que se agregan a las clases son exportado (o importan) desde el archivo DLL de extensión MFC. Por ejemplo, al derivar una clase con `DECLARE_DYNAMIC`, la macro se expandirá para agregar una `CRuntimeClass` variable miembro a la clase. Si se omiten estas cuatro líneas puede provocar que el archivo DLL puede compilarse o vincularse incorrectamente o causar un error cuando la aplicación cliente que se vincula a la DLL.

Al compilar el archivo DLL, el vinculador utiliza el archivo .def para crear un archivo de exportación (.exp) y un archivo de biblioteca (.lib) de importación. El vinculador utiliza, a continuación, el archivo de exportación para crear el archivo DLL. Archivos ejecutables que se vinculan implícitamente al archivo DLL se vinculan a la biblioteca de importación cuando se generan.

Tenga en cuenta que MFC utiliza archivos .def para exportar funciones y clases desde MFCx0.dll.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)

- [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [archivos .def](../build/reference/module-definition-dot-def-files.md)

- [Reglas para instrucciones de definición de módulo](../build/reference/rules-for-module-definition-statements.md)

- [Nombres representativos](../build/reference/decorated-names.md)

- [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](../build/mutual-imports.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)