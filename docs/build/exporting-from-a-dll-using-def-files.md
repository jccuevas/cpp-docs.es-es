---
title: Exportar desde un archivo DLL mediante archivos DEF
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078523"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportar desde un archivo DLL mediante archivos DEF

Un archivo DEF o de definición de módulos (*.def) es un archivo de texto que contiene una o más instrucciones de módulo que describen varios atributos de un archivo DLL. Si no usa la palabra clave **__declspec(dllexport)** para exportar las funciones del archivo DLL, el archivo DLL requiere un archivo DEF.

Un archivo DEF mínimo debe contener las siguientes instrucciones de definición de módulo:

- La primera instrucción del archivo debe ser LIBRARY. Esta instrucción identifica el archivo DEF como perteneciente a un archivo DLL. La instrucción LIBRARY va seguida del nombre del archivo DLL. El enlazador coloca este nombre en la biblioteca de importación del archivo DLL.

- La instrucción EXPORTS enumera los nombres y, opcionalmente, los valores ordinales de las funciones exportadas por el archivo DLL. Para asignar a la función un valor ordinal, se debe agregar un signo de arroba (@) y un número detrás del nombre de la función. Cuando se especifican valores ordinales, deben estar en el intervalo comprendido entre 1 y N, donde N es el número de funciones exportadas por el archivo DLL. Si quiere exportar funciones por ordinal, vea [Exportación de funciones desde un archivo DLL por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) así como este tema.

Por ejemplo, un archivo DLL que contiene el código para implementar un árbol de búsqueda binaria podría ser similar al siguiente:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Si usa el [Asistente para archivos DLL de MFC](../mfc/reference/mfc-dll-wizard.md) para crear un archivo DLL de MFC, el asistente crea un archivo DEF de esquema y lo agrega automáticamente al proyecto. Agregue a este archivo los nombres de las funciones que se van a exportar. Para los archivos DLL que no son de MFC, cree el archivo DEF y agréguelo al proyecto. Después, vaya a **Proyecto** > **Propiedades** > **Enlazador** > **Entrada** > **Archivo de definición de módulos** y escriba el nombre del archivo DEF. Repita este paso para cada configuración y plataforma, o bien para todos a la vez si selecciona **Configuración = Todas las configuraciones** y **Plataforma = Todas las plataformas**.

Si va a exportar funciones en un archivo de C++, tendrá que colocar los nombres representativos en el archivo DEF o definir las funciones exportadas con la vinculación de C estándar mediante extern "C". Si tiene que colocar los nombres representativos en el archivo DEF, puede obtenerlos mediante la herramienta [DUMPBIN](../build/reference/dumpbin-reference.md) o la opción del enlazador [/MAP](../build/reference/map-generate-mapfile.md). Tenga en cuenta que los nombres representativos generados por el compilador son específicos del compilador. Si coloca los nombres representativos generados por el compilador de Microsoft C++ (MSVC) en un archivo DEF, las aplicaciones que se vinculan al archivo DLL también se deben compilar con la misma versión de MSVC para que los nombres representativos de la aplicación que realiza la llamada coincidan con los nombres exportados en el archivo DEF de la DLL.

> [!NOTE]
> Un archivo DLL compilado con Visual Studio 2015 puede ser utilizado por aplicaciones compiladas con Visual Studio 2017 o Visual Studio 2019.

Si va a compilar un [archivo DLL de extensión](../build/extension-dlls-overview.md) y a exportar con un archivo DEF, coloque el código siguiente al principio y al final de los archivos de encabezado que contienen las clases exportadas:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Estas líneas garantizan que las variables de MFC que se usan internamente o que se agregan a las clases se exportan (o importan) desde el archivo DLL de extensión de MFC. Por ejemplo, al derivar una clase mediante `DECLARE_DYNAMIC`, la macro se expande para agregar una variable miembro `CRuntimeClass` a la clase. Si se omiten estas cuatro líneas, es posible que el archivo DLL se compile o se vincule incorrectamente, o bien que se produzca un error cuando la aplicación cliente se vincula al archivo DLL.

Al compilar el archivo DLL, el enlazador usa el archivo DEF para crear un archivo de exportación (.exp) y un archivo de biblioteca de importación (.lib). Después, el enlazador usa el archivo de exportación para compilar el archivo DLL. Los ejecutables que se vinculan de forma implícita al archivo DLL se vinculan a la biblioteca de importación cuando se compilan.

Tenga en cuenta que MFC usa archivos DEF para exportar funciones y clases desde MFCx0.dll.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportación de funciones de C para usarlas en ejecutables del lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinación del método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicialización de un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Archivos .def](reference/module-definition-dot-def-files.md)

- [Reglas para instrucciones de definición de módulos](reference/rules-for-module-definition-statements.md)

- [Nombres representativos](reference/decorated-names.md)

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
