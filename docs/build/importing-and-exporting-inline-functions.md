---
title: "Importar y exportar funciones inline | Microsoft Docs"
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
  - "DLL [C++], exportar desde"
  - "DLL [C++], importar"
  - "exportar funciones [C++], funciones inline"
  - "funciones [C++], exportar"
  - "funciones [C++], importar"
  - "importar funciones [C++]"
  - "importar funciones inline [C++]"
  - "inline (funciones) [C++], exportar"
  - "inline (funciones) [C++], importar"
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Importar y exportar funciones inline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones importadas deben definirse como funciones inline.  El efecto es parecido al resultante de definir una función estándar inline; las llamadas a la función se expanden al código en línea, de forma parecida a cómo lo hace una macro.  Esto es especialmente útil como forma de ofrecer compatibilidad con las clases de C\+\+ en un archivo DLL que puede incluir en línea algunas de sus funciones miembro para aumentar la eficacia.  
  
 Una característica de una función inline importada es que puede utilizar su dirección en C\+\+.  El compilador devuelve la dirección de la copia de la función inline que reside en el archivo DLL.  Otra característica de las funciones inline importadas es que pueden inicializar datos locales estáticos de la función importada \(y no datos globales importados\).  
  
> [!CAUTION]
>  Debe tener cuidado al proporcionar funciones inline importadas, ya que podrían producir conflictos entre versiones.  Una función inline se expande en el código de la aplicación; por tanto, si después vuelve a escribir la función, no se actualizará a menos que se vuelva a compilar la aplicación. Normalmente, las funciones de archivos DLL pueden actualizarse sin recompilar las aplicaciones que las utilizan.  
  
## ¿Qué desea hacer?  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos .DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)