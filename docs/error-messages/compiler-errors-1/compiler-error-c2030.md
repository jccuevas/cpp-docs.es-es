---
title: "Error del compilador C2030 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2030"
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'  
  
 Una clase de Windows en tiempo de ejecución declarada como `sealed` no puede tener un destructor privado protegido.  En tipos sealed solo se permiten destructores no virtuales privados y virtuales públicos.  Para obtener más información, vea [Ref \(Clases y structs\)](../Topic/Ref%20classes%20and%20structs%20\(C++-CX\).md).  
  
 Para corregir este error, cambie la accesibilidad del destructor.