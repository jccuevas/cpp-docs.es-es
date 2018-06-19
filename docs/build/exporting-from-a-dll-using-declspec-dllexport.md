---
title: Exportar desde un archivo DLL Mediante__declspec (dllexport) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllexport
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6ab1d11c117c75633ce4ab836965449c4cc6ca1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368553"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Exportar desde un archivo DLL mediante __declspec(dllexport)
Microsoft introducida **__export** en la versión del compilador de 16 bits de Visual C++ para permitir que el compilador genera automáticamente los nombres de exportación y colocarlos en un archivo .lib. Este archivo .lib puede utilizarse como una biblioteca .lib estática para vincularlo a un archivo DLL.  
  
 En las versiones del compilador más reciente, puede exportar datos, funciones, clases o funciones miembro de clase desde un archivo DLL mediante la **__declspec (dllexport)** (palabra clave). **__declspec (dllexport)** agrega la directiva de exportación al archivo de objeto no es necesario utilizar un archivo .def.  
  
 Esta conveniencia es más evidente cuando se intenta exportar nombres de función de C++ representativos. Porque no hay ninguna especificación estándar para la decoración de nombres, el nombre de una función exportada podría cambiar entre las versiones del compilador. Si usa **__declspec (dllexport)**, volver a compilar el archivo DLL y los archivos .exe dependientes solo es necesario para cuenta para los cambios de convención de nomenclatura.  
  
 Muchas directivas de exportación, como los ordinales, NONAME y PRIVATE, pueden realizarse solo en un archivo .def, y no hay ninguna manera de especificar estos atributos sin un archivo .def. No obstante, el uso **__declspec (dllexport)** además de usar un .def archivo no producirán errores de compilación.  
  
 Para exportar funciones, la **__declspec (dllexport)** palabra clave debe aparecer a la izquierda de la palabra clave de convención de llamada, si se especifica una palabra clave. Por ejemplo:  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 Para exportar todos los miembros de datos públicos y las funciones de miembro en una clase, la palabra clave debe aparecer a la izquierda del nombre de clase como sigue:  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` no se puede aplicar a una función con el `__clrcall` convención de llamada.  
  
 Al compilar el archivo DLL, normalmente se crea un archivo de encabezado que contiene los prototipos de función o las clases que va a exportar y agregue **__declspec (dllexport)** a las declaraciones en el archivo de encabezado. Para que el código sea más legible, defina una macro para **__declspec (dllexport)** y utilice la macro con cada símbolo que se va a exportar:  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec (dllexport)** almacena los nombres en la tabla de exportación de los archivos DLL de función. Si desea optimizar el tamaño de la tabla, vea [exportar funciones desde un archivo DLL por Ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
> [!NOTE]
>  Al trasladar código de origen del archivo DLL de Win16 a Win32, reemplace cada instancia de **__export** con **__declspec (dllexport)**.  
  
 Como referencia, buscar el archivo de encabezado Winbase.h de Win32. Este archivo contiene ejemplos de **__declspec (dllimport)** uso.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables de C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La palabra clave __declspec](../cpp/declspec.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)