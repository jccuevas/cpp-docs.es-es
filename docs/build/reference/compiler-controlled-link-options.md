---
title: "Opciones de LINK controladas por el compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador) [C++], controlar el vinculador"
  - "cl.exe (compilador) [C++], características que afectan a la vinculación"
  - "LINK (herramienta) [C++], opciones controladas por el compilador"
  - "vinculador [C++], CL (control del compilador)"
  - "vincular [C++], afectado por características de CL"
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Opciones de LINK controladas por el compilador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

A menos que se especifique la opción \/c, el compilador de CL llamará automáticamente a LINK.  CL proporciona cierto control sobre el compilador por medio de argumentos y opciones de la línea de comandos.  En la tabla siguiente se resumen las características de CL que afectan a la vinculación.  
  
|Especificación de CL|Acción de CL que afecta a LINK|  
|--------------------------|------------------------------------|  
|Cualquier extensión de nombre de archivo aparte de .c, .cxx, .cpp o .def|Pasa a LINK un nombre de archivo como entrada|  
|*nombredearchivo*.def|Pasa \/DEF:*nombredearchivo*.def|  
|\/F`number`|Pasa \/STACK:`number`|  
|\/Fd*nombredearchivo*|Pasa \/PDB:*nombredearchivo*|  
|\/Fe*nombredearchivo*|Pasa \/OUT:*nombredearchivo*|  
|\/Fm*nombredearchivo*|Pasa \/MAP:*nombredearchivo*|  
|\/Gy|Crea funciones empaquetadas \(COMDAT\); habilita la vinculación en el nivel de función|  
|\/LD|Pasa \/DLL|  
|\/LDd|Pasa \/DLL|  
|\/link|Pasa el resto de la línea de comandos a LINK|  
|\/MD o \/MT|Sitúa el nombre de la biblioteca predeterminada en el archivo .obj|  
|\/MDd o \/MTd|Sitúa un nombre de biblioteca predeterminada en el archivo .obj.  Define el símbolo **\_DEBUG**|  
|\/nologo|Pasa \/NOLOGO|  
|\/Zd|Pasa \/DEBUG|  
|\/Zi o \/Z7|Pasa \/DEBUG|  
|\/Zl|Omite el nombre de la biblioteca predeterminada en el archivo .obj|  
  
 Para obtener más información, vea [Opciones del compilador](../../build/reference/compiler-options.md).  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)