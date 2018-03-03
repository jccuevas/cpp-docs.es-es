---
title: Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0511ae4c16332b2a8e98c2319e148249b66c8461
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Exportar funciones de C++ para utilizarlas en ejecutables creados en C  
  
Si desea tener acceso a funciones de un archivo DLL programadas en C++ desde un módulo programado en C, deberá declarar estas funciones con una vinculación C, en lugar de una vinculación C++. A menos que se especifique lo contrario, el compilador de C++ utiliza la asignación de nombres con seguridad de tipos de C++ (también llamada decoración de nombres) y las convenciones de llamada de C++, que pueden resultar difíciles de llamar desde C.  
  
Para especificar la vinculación de C, especifique `extern "C"` para las declaraciones de función. Por ejemplo:  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables de C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)