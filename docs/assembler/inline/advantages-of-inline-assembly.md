---
title: "Ventajas del ensamblado alineado | Microsoft Docs"
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
  - "ensamblador [C++], ventajas"
  - "ensamblado alineado [C++], acerca del ensamblado alineado"
  - "ensamblado alineado [C++], utilizar"
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Ventajas del ensamblado alineado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Dado que el ensamblador alineado no requiere pasos de ensamblado y vínculo independientes y de vínculo, es más aconsejable que un ensamblador independiente.  El código de ensamblado alineado puede utilizar cualquier nombre de variable o de función de C que esté en el ámbito, por lo que resulta fácil integrarlo con el código C del programa.  Dado que el código de ensamblado se puede combinar alineado con instrucciones de C o C\+\+, puede realizar tareas complicadas o imposibles en C o C\+\+.  
  
 Entre los usos de ensamblado alineado se incluyen:  
  
-   Escritura de funciones en lenguaje de ensamblado.  
  
-   Optimización de punto en secciones de código críticas en cuanto a velocidad.  
  
-   Suministro de acceso directo de hardware para los controladores de dispositivo.  
  
-   Escritura de código de prólogo y epílogo para llamadas "naked".  
  
 El ensamblado alineado es una herramienta para fines especiales.  Si piensa migrar una aplicación a equipos diferentes, es probable que desee colocar código específico del equipo en un módulo independiente.  Dado que el ensamblador alineado no admite todas las directivas de macro y datos de Microsoft Macro Assembler \(MASM\), puede que le resulte más conveniente utilizar MASM para dichos módulos.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)