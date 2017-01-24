---
title: "Importar y exportar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) (palabra clave) [C++]"
  - "DLL [C++], exportar desde"
  - "DLL [C++], importar"
  - "exportar DLL [C++]"
  - "importar archivos DLL [C++]"
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Importar y exportar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede importar símbolos públicos a una aplicación o exportar funciones de un archivo DLL mediante dos métodos:  
  
-   Utilizar un archivo de definición de módulo \(.def\) al compilar el archivo DLL.  
  
-   Utilizar las palabras clave **\_\_declspec\(dllimport\)** o **\_\_declspec\(dllexport\)** de una definición de función en la aplicación principal  
  
## Utilizar un archivo .def  
 Un archivo de definición de módulo \(.def\) es un archivo de texto que contiene una o varias instrucciones de módulo que describen distintos atributos de un archivo DLL.  Si no utiliza **\_\_declspec\(dllimport\)** o **\_\_declspec\(dllexport\)** para exportar funciones de un archivo DLL, este archivo requiere un archivo .def.  
  
 Puede utilizar archivos .def para [importar a una aplicación](../build/importing-using-def-files.md) o para [exportar desde un archivo DLL](../build/exporting-from-a-dll-using-def-files.md).  
  
## Utilizar \_\_declspec  
 Visual C\+\+ utiliza **\_\_declspec\(dllimport\)** y **\_\_declspec\(dllexport\)** para reemplazar la palabra clave **\_\_export** utilizada previamente en las versiones de 16 bits de Visual C\+\+.  
  
 No tiene que utilizar **\_\_declspec\(dllimport\)** para que el código se compile correctamente, pero si lo hace, el compilador podrá generar código de mejor calidad.  El compilador puede generar código de mejor calidad porque puede determinar si una función existe o no en un archivo DLL; por tanto, puede producir código que omita un nivel de direccionamiento indirecto que existiría normalmente en una función que cruza un límite de archivo DLL.  Sin embargo, debe utilizar **\_\_declspec\(dllimport\)** para importar variables utilizadas en un archivo DLL.  
  
 Con la sección EXPORTS apropiada del archivo .def, **\_\_declspec\(dllexport\)** no es necesaria.  **\_\_declspec\(dllexport\)** se agregó para proporcionar una forma fácil de exportar funciones desde un archivo .exe o .dll sin utilizar ningún archivo .def.  
  
 El formato de Win32 Portable Executable está diseñado para minimizar el número de páginas que hay que retocar para corregir importaciones.  Para ello, coloca todas las direcciones de importación de cualquier programa en un lugar denominado Tabla de direcciones de importación.  Esto permite al cargador modificar únicamente una o dos páginas cuando se obtiene acceso a estas importaciones.  
  
## ¿Qué desea hacer?  
  
-   [Importar a una aplicación](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)