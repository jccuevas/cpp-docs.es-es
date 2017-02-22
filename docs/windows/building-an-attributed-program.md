---
title: "Building an Attributed Program | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tlb files"
  - "MIDL"
  - "MIDL, linker output"
  - "IDL files"
  - "tlb files, building attributed programs"
  - ".tlb files, building attributed programs"
  - "IDL files, building"
  - "attributes [C++], building type libraries and .idl files"
  - ".tlb files"
  - ".idl files, building"
  - "type libraries, linker options for building"
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Building an Attributed Program
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Después de incluir atributos de Visual C\+\+ en el código fuente, puede que el compilador de Visual C\+\+ para mostrar una biblioteca de tipos y el archivo .idl automáticamente.  Ayuda siguiente de las opciones del vinculador se compilan los archivos .tlb y .idl:  
  
-   [\/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [\/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [\/MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [\/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 Algunos proyectos contienen varios archivos de la independiente .idl.  Estos se utilizan para mostrar dos o más archivos .tlb y enlazarlos opcionalmente en el bloque de recursos.  Este escenario no se admite actualmente en Visual C\+\+.  
  
 Además, el vinculador de Visual C\+\+ generará toda la información de atributos IDL\-relacionada en un solo archivo de MIDL.  No hay manera de generar dos bibliotecas de tipos de un solo proyecto.  
  
## Vea también  
 [Concepts](../windows/attributed-programming-concepts.md)