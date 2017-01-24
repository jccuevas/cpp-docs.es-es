---
title: "Generaci&#243;n de manifiestos en la l&#237;nea de comandos | Microsoft Docs"
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
  - "herramienta de manifiesto (mt.exe)"
  - "manifiestos [C++]"
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Generaci&#243;n de manifiestos en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al compilar aplicaciones de C\/C\+\+ desde la línea de comandos mediante nmake o herramientas similares, el manifiesto se crea después de que el vinculador haya procesado todos los archivos objeto y compilado el archivo binario final.  El vinculador recopila información de ensamblado almacenada en los archivos objeto y combina esta información en un archivo de manifiesto final.  De forma predeterminada el vinculador generará un archivo denominado \<binary\_name\>.\<extenson\>.manifest el archivo binario final.  El vinculador no incrusta un archivo de manifiesto dentro del archivo binario y sólo puede generar un manifiesto como un archivo externo.  Existen varios modos de incrustar un manifiesto dentro del archivo binario final, por ejemplo usar la [Herramienta Manifiesto \(mt.exe\)](http://msdn.microsoft.com/library/aa375649) o compilar el manifiesto en un archivo de recursos.  Es importante tener en cuenta que se deben seguir unas reglas específicas al incrustar un manifiesto dentro del archivo binario final para habilitar características como la vinculación incremental, la firma y editar y continuar.  Estas y otras opciones se tratan en [Cómo: Incrustar un manifiesto en una aplicación de C\/C\+\+](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) al compilar en la línea de comandos.  
  
## Vea también  
 [Manifiestos](http://msdn.microsoft.com/library/aa375365)   
 [\/INCREMENTAL \(Vincular de forma incremental\)](../build/reference/incremental-link-incrementally.md)   
 [Ensamblados de nombre seguro \(Firma de ensamblados\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Editar y continuar](../Topic/Edit%20and%20Continue.md)   
 [Introducción a la generación de manifiestos para los programas de C\/C\+\+](../build/understanding-manifest-generation-for-c-cpp-programs.md)