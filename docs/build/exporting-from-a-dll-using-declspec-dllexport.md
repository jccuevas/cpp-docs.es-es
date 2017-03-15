---
title: "Exportar desde un archivo DLL mediante __declspec(dllexport) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dllexport"
  - "__declspec"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllexport) (palabra clave) [C++]"
  - "exportar directivas [C++]"
  - "exportar DLL [C++], __declspec(dllexport) (palabra clave)"
  - "nombres [C++], exportar DLL por"
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Exportar desde un archivo DLL mediante __declspec(dllexport)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft introdujo **\_\_export** en la versión del compilador de 16 bits de Visual C\+\+ para que el compilador pudiera generar automáticamente los nombres de exportación y colocarlos en un archivo .lib.  Este archivo .lib puede utilizarse de la misma manera que una biblioteca .lib estática para vincularlo a un archivo DLL.  
  
 En las versiones del compilador más recientes, se pueden exportar datos, funciones, clases o funciones miembro de clase desde un archivo DLL mediante la palabra clave **\_\_declspec\(dllexport\)**.  **\_\_declspec\(dllexport\)** agrega la directiva de exportación al archivo objeto para que no tenga que utilizar un archivo .def.  
  
 Esta conveniencia es más aparente cuando se intenta exportar nombres de función representativos de C\+\+.  No hay ninguna especificación estándar para la creación de nombres representativos, por lo que el nombre de una función exportada podría cambiar en distintas versiones de compilador.  Si utiliza **\_\_declspec\(dllexport\)**, sólo será necesario volver a compilar los archivos DLL y los archivos.exe dependientes para realizar los cambios de convención de nomenclatura.  
  
 Muchas directivas de exportación, como los ordinales, NONAME y PRIVATE, sólo pueden utilizarse en un archivo .def, y no hay ninguna forma de especificar estos atributos sin un archivo .def.  Sin embargo, si utiliza **\_\_declspec\(dllexport\)** además de un archivo .def, no se producirán errores de compilación.  
  
 Para exportar funciones, la palabra clave **\_\_declspec\(dllexport\)** deberá aparecer a la izquierda de la palabra clave de convención de llamada si se especifica una palabra clave.  Por ejemplo:  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 Para exportar todos los miembros de datos públicos y las funciones miembro de una clase, la palabra clave deberá aparecer a la izquierda del nombre de clase de la manera siguiente:  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` no se puede aplicar a una función con la convención de llamada `__clrcall`.  
  
 Al compilar el archivo DLL, generalmente crea un archivo de encabezado que contiene los prototipos de función o las clases que va a exportar, y agrega **\_\_declspec\(dllexport\)** a las declaraciones del archivo de encabezado.  Para hacer que el código sea más legible, defina una macro para **\_\_declspec\(dllexport\)** y después utilice la macro con cada símbolo que exporte:  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **\_\_declspec\(dllexport\)** almacena nombres de función en la tabla de exportación del archivo DLL.  Si desea optimizar el tamaño de la tabla, vea [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
> [!NOTE]
>  Al trasladar el código fuente del archivo DLL de Win16 a Win32, reemplace cada instancia de **\_\_export** por **\_\_declspec\(dllexport\)**.  
  
 Como referencia, busque en el archivo de encabezado Winbase.h de Win32.  Este archivo contiene ejemplos del uso de **\_\_declspec\(dllimport\)**.  
  
## ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [La palabra clave \_\_declspec](../cpp/declspec.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)