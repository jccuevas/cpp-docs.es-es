---
title: "Archivos de definici&#243;n de m&#243;dulos (.Def) | Microsoft Docs"
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
  - ".def (archivos)"
  - "def (archivos)"
  - "archivos de definición de módulos"
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos de definici&#243;n de m&#243;dulos (.Def)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos de definición de módulos \(.def\) proporcionan al vinculador información sobre exportaciones, atributos y otros datos del programa que se va a vincular.  Un archivo .def resulta de gran utilidad para compilar una DLL.  Puesto que existen [opciones del vinculador](../../build/reference/linker-options.md) que se pueden utilizar en lugar de las instrucciones de definición de módulos, los archivos .def normalmente no son necesarios.  También se puede utilizar [\_\_declspec\(dllexport\)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) para especificar funciones exportadas.  
  
 Puede invocar a un archivo .def durante la fase de vinculación con la opción [\/DEF \(archivo de definiciones de módulo\)](../../build/reference/def-specify-module-definition-file.md) del vinculador.  
  
 Si está compilando un archivo .exe sin exportaciones, el uso de un archivo .def producirá un archivo de salida más grande y de carga más lenta.  
  
 Para obtener un ejemplo, vea [Exportar desde un archivo DLL mediante archivos DEF](../../build/exporting-from-a-dll-using-def-files.md).  
  
 Vea las secciones siguientes para obtener más información:  
  
-   [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [NAME](../../build/reference/name-c-cpp.md)  
  
-   [SECTIONS](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [VERSION](../../build/reference/version-c-cpp.md)  
  
-   [Palabras reservadas](../../build/reference/reserved-words.md)  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/es-es/56a3bb8f-0181-4989-bab4-a07ba950ab08)