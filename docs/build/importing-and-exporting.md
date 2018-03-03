---
title: "Importación y exportación | Documentos de Microsoft"
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
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c0727002e264f3b0cfe39b763c29fd70725b982
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting"></a>Importar y exportar
Puede importar símbolos públicos en una aplicación o exportar funciones desde un archivo DLL mediante dos métodos:  
  
-   Usar un archivo de definición (.def) de módulo al generar el archivo DLL  
  
-   Usar las palabras clave **__declspec (dllimport)** o **__declspec (dllexport)** en una definición de función en la aplicación principal  
  
## <a name="using-a-def-file"></a>Utilizar un archivo .def  
 Un archivo de definición de módulos (.def) es un archivo de texto que contiene una o varias instrucciones de módulo que describen distintos atributos de un archivo DLL. Si no usa **__declspec (dllimport)** o **__declspec (dllexport)** para exportar funciones de un archivo DLL, el archivo DLL requiere un archivo .def.  
  
 Puede utilizar archivos .def para [importar a una aplicación](../build/importing-using-def-files.md) o a [exportar desde un archivo DLL](../build/exporting-from-a-dll-using-def-files.md).  
  
## <a name="using-declspec"></a>Utilizar __declspec  
 Usos visuales C++ **__declspec (dllimport)** y **__declspec (dllexport)** para reemplazar el **__export** palabra clave utilizada previamente en las versiones de 16 bits de Visual C++.  
  
 No es necesario usar **__declspec (dllimport)** para que el código para compilarse correctamente, pero si lo hace, permite al compilador que genere código de mejor calidad. El compilador es capaz de generar código de mejor calidad porque puede determinar si existe una función en un archivo DLL o no es así, lo que permite al compilador que cree código que omite un nivel de direccionamiento indirecto que normalmente aparecería en una llamada de función que cruza un límite DLL. Sin embargo, debe usar **__declspec (dllimport)** para importar las variables utilizadas en un archivo DLL.  
  
 Con la sección EXPORTS de archivo .def apropiado, **__declspec (dllexport)** no es necesario. **__declspec (dllexport)** se agregó para proporcionar una manera fácil de exportar funciones desde un archivo .exe o .dll sin utilizar un archivo .def.  
  
 El formato de archivo Portable ejecutable de Win32 está diseñado para minimizar el número de páginas que se debe tocar para corregir importaciones. Para ello, coloca todas las direcciones de importación para cualquier programa en un lugar denominado tabla de direcciones de importación. Esto permite que el cargador para modificar sólo una o dos páginas al tener acceso a estas importaciones.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Importar a una aplicación](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)