---
title: Exportar funciones de C para utilizarlas en C o archivos ejecutables de lenguaje C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e92ef965372d1bf0b0272b5a962091ff0ae88e1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportar funciones de C para utilizarlas en ejecutables creados en C o C++  
  
Si dispone de funciones en un archivo DLL escrita en C, que desea tener acceso desde un lenguaje C o un módulo de lenguaje C++, debe utilizar el **__cplusplus** macro de preprocesador para determinar el idioma que se está compilando y, a continuación, declarar estas funciones con vinculación de C si se utiliza desde un módulo de lenguaje C++. Si utiliza esta técnica y proporciona archivos de encabezado para el archivo DLL, estas funciones se pueden usar los usuarios de C y C++ sin cambios.  
  
El código siguiente muestra un archivo de encabezado que puede usarse en aplicaciones de cliente de C y C++:  
  
```h  
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
  
Si necesita vincular las funciones de C para el ejecutable de C++ y los archivos de encabezado de la declaración de función no han utilizado la técnica anterior, en el archivo de código fuente de C++, realice lo siguiente para evitar que el compilador decorando los nombres de función de C:  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)