---
title: "Definición de módulo (. Archivos DEF) | Documentos de Microsoft"
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
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 49f5eb5b75bad22b59cb4fbb98554bbfd44d13b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="module-definition-def-files"></a>Archivos de definición de módulos (.Def)
Archivos de definición de módulos (.def) proporcionan al vinculador información sobre exportaciones, atributos y otra información sobre el programa para vincularse. Un archivo .def es muy útil cuando se crea un archivo DLL. Dado que hay [opciones del vinculador](../../build/reference/linker-options.md) que se puede utilizar en lugar de las instrucciones de definición de módulos, archivos .def normalmente no son necesarios. También puede usar [__declspec (dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) como una manera de especificar las funciones exportadas.  
  
 Puede invocar un archivo .def durante la fase de vinculación con el [/DEF (especificar archivo de definición de módulos)](../../build/reference/def-specify-module-definition-file.md) opción del vinculador.  
  
 Si está generando un archivo .exe que no tiene exportaciones, utilizar un archivo .def hará que la carga de grandes y más lento de archivos de salida.  
  
 Para obtener un ejemplo, vea [exportar desde un archivo DLL mediante archivos DEF](../../build/exporting-from-a-dll-using-def-files.md).  
  
 Consulte las secciones siguientes para obtener más información:  
  
-   [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [NOMBRE](../../build/reference/name-c-cpp.md)  
  
-   [SECCIONES](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [VERSIÓN](../../build/reference/version-c-cpp.md)  
  
-   [Palabras reservadas](../../build/reference/reserved-words.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)  