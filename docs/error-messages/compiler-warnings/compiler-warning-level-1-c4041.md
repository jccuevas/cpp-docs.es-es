---
title: "Advertencia del compilador (nivel 1) C4041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4041"
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador : se va a finalizar el resultado del explorador  
  
 La información del explorador supera el límite del compilador.  
  
 Esta advertencia puede deberse a la compilación con [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) \(información del explorador con variables locales\).  
  
### Para corregir mediante las siguientes posibles soluciones  
  
1.  Compile con \/Fr \(información del explorador sin variables locales\).  
  
2.  Deshabilite el resultado del explorador \(compile sin \/FR o \/Fr\).