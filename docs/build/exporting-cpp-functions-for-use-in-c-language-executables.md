---
title: "Exportar funciones de C++ para utilizarlas en ejecutables creados en C | Microsoft Docs"
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
  - "exportar DLL [C++], funciones de C++ en ejecutables de C"
  - "exportar funciones [C++], funciones de C++ en ejecutables de C"
  - "funciones [C++], funciones de C++ en ejecutables de C"
  - "funciones [C++], exportar"
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exportar funciones de C++ para utilizarlas en ejecutables creados en C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si desea tener acceso a funciones de un archivo DLL programadas en C\+\+ desde un módulo programado en C, deberá declarar estas funciones con una vinculación C, en lugar de una vinculación C\+\+.  A menos que se especifique lo contrario, el compilador de C\+\+ utiliza la asignación de nombres con seguridad de tipos de C\+\+ \(también llamada decoración de nombres\) y las convenciones de llamada de C\+\+, que pueden resultar difíciles de llamar desde C.  
  
 Para establecer la vinculación C, debe especificar **extern** "**C**" para las declaraciones de función.  Por ejemplo:  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Especificaciones de vinculación](http://msdn.microsoft.com/es-es/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)