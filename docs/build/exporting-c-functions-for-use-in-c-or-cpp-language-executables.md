---
title: "Exportar funciones de C para utilizarlas en ejecutables creados en C o C++ | Microsoft Docs"
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
  - "__cplusplus (macro)"
  - "exportar DLL [C++], funciones de C en ejecutables de C++"
  - "exportar funciones [C++], funciones de C en ejecutables de C++"
  - "funciones [C], ejecutables de C++ o C y"
  - "funciones [C], exportar"
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exportar funciones de C para utilizarlas en ejecutables creados en C o C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si desea tener acceso a funciones de un archivo DLL programadas en C desde un módulo programado C o C\+\+, debe utilizar la macro de preprocesador **\_\_cplusplus** para determinar en qué lenguaje se va a compilar y, después, declarar estas funciones con la vinculación C si se van a utilizar en un módulo programado en C\+\+.  Si utiliza esta técnica y proporciona archivos de encabezado para el archivo DLL, los usuarios de C y C\+\+ pueden realizar estas funciones hacer cambios.  
  
 El siguiente fragmento de código muestra un archivo de encabezado que se puede utilizar en aplicaciones cliente programadas en C y C\+\+:  
  
```  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 Si tiene que vincular funciones programadas en C a un ejecutable programado en C\+\+ y los archivos de encabezado de la declaración de función no han utilizado la técnica anterior, haga lo siguiente en el archivo de código fuente de C\+\+ para evitar que el compilador decore los nombres de funciones programadas en C:  
  
```  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Especificaciones de vinculación](http://msdn.microsoft.com/es-es/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)