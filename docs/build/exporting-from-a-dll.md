---
title: "Exportar desde un archivo DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exportar DLL [C++]"
  - "DLL [C++], exportar desde"
  - "exportar DLL [C++]"
  - "exportar DLL [C++], acerca de exportar desde DLL"
  - "exportar funciones [C++], DLL (exportar desde)"
  - "exportaciones de tablas [C++]"
  - "funciones [C++], exportar"
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Exportar desde un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos .DLL tienen un diseño muy similar al de los archivos .exe, con una diferencia importante: los archivos DLL contienen una tabla de exportaciones.  La tabla de exportaciones contiene el nombre de cada función exportada desde el archivo DLL a otros ejecutables.  Estas funciones son los puntos de entrada al archivo DLL; sólo se puede obtener acceso a las funciones de la tabla de exportaciones mediante otros ejecutables.  Las demás funciones del archivo DLL son funciones privadas del archivo DLL.  La tabla de exportaciones de un archivo DLL puede verse mediante la herramienta [DUMPBIN](../build/reference/dumpbin-reference.md) con la opción \/EXPORTS.  
  
 Puede exportar funciones desde un archivo DLL de dos maneras diferentes:  
  
-   Creando un archivo de definición de módulo \(.def\) y utilizándolo al generar el archivo DLL.  Se debe utilizar este enfoque si se desea [exportar funciones desde el archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
-   Utilizando la palabra clave **\_\_declspec\(dllexport\)** en la definición de la función.  
  
 Al exportar funciones con estos métodos, asegúrese de que utiliza la convención de llamada [\_\_stdcall](../cpp/stdcall.md).  
  
## ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Importar a una aplicación](../build/importing-into-an-application.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)