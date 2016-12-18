---
title: "/RANGE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/RANGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RANGE (opción de dumpbin)"
  - "-RANGE (opción de dumpbin)"
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RANGE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Modifica el resultado de dumpbin cuando se utiliza con otras opciones de dumpbin, como \/RAWDATA o \/DISASM.  
  
## Sintaxis  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## Marcas  
 **vaMin**  
 La dirección virtual en la que desea que comience la operación dumpbin.  
  
 **vaMax** \(opcional\)  
 La dirección virtual en la que desea que finalice la operación dumpbin.  Si no se especifica, dumpbin irá al final del archivo.  
  
## Comentarios  
 Para ver las direcciones virtuales para una imagen, use el archivo de asignaciones correspondiente a la imagen \(RVA \+ Base\), la opción **\/DISASM** o **\/HEADERS** de dumpbin, o la ventana Desensamblado del depurador de Visual Studio.  
  
## Ejemplo  
 En este ejemplo, **\/range** se utiliza para modificar la presentación de la opción **\/disasm**.  En este ejemplo, el valor inicial se expresa como un número decimal y el valor final se especifica como un número hexadecimal.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)