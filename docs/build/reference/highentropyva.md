---
title: "/HIGHENTROPYVA | Microsoft Docs"
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
  - "/HIGHENTROPYVA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/HIGHENTROPYVA editbin (opción)"
  - "HIGHENTROPYVA editbin (opción)"
  - "-HIGHENTROPYVA editbin (opción)"
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HIGHENTROPYVA
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones \(ASLR\) de 64 bits de alta entropía.  
  
```  
  
/HIGHENTROPYVA[:NO]  
  
```  
  
## Comentarios  
 Esta opción modifica el encabezado de un archivo .dll o .exe para indicar si se admite ASLR con direcciones de 64 bits.  Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede reorganizar los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits.  Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.  
  
 De forma predeterminada, el enlazador establece esta opción para las imágenes ejecutables de 64 bits.  Para establecer esta opción, también debe establecerse la opción [\/DYNAMICBASE](../../build/reference/dynamicbase.md).  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [\/DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Defensas de seguridad de software de ISV de Windows](http://msdn.microsoft.com/library/bb430720.aspx)