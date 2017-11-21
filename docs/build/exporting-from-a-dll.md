---
title: Exportar desde un archivo DLL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a591628d74320dee7868b0c689bd4d61bb19073d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="exporting-from-a-dll"></a>Exportar desde un archivo DLL  
  
Los archivos .DLL tienen un diseño muy similar al de los archivos .exe, con una diferencia importante: los archivos DLL contienen una tabla de exportaciones. La tabla de exportaciones contiene el nombre de cada función exportada desde el archivo DLL a otros ejecutables. Estas funciones son los puntos de entrada al archivo DLL; sólo se puede obtener acceso a las funciones de la tabla de exportaciones mediante otros ejecutables. Las demás funciones del archivo DLL son funciones privadas del archivo DLL. La tabla de exportaciones de un archivo DLL puede verse mediante la [DUMPBIN](../build/reference/dumpbin-reference.md) herramienta con la opción/EXPORTS.  
  
 Puede exportar funciones desde un archivo DLL de dos maneras diferentes:  
  
-   Creando un archivo de definición de módulo (.def) y utilizándolo al generar el archivo DLL. Use este método si desea [exportar funciones desde el archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
-   Use la palabra clave **__declspec (dllexport)** en la definición de la función.  
  
 Al exportar funciones con estos métodos, asegúrese de usar la [__stdcall](../cpp/stdcall.md) convención de llamada.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables de C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Importar a una aplicación](../build/importing-into-an-application.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)