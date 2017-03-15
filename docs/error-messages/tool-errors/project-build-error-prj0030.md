---
title: "Error PRJ0030 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0030"
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error PRJ0030 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error de expansión de macro.La recursividad de evaluación superó los 32 niveles para $\(macro\).  
  
 Este error se produce por recursividad en las macros.  Por ejemplo, si establece la propiedad **Directorio intermedio** \(vea la [Página de propiedades General \(Proyecto\)](../../ide/general-property-page-project.md)\) en $\(IntDir\), se obtendrá recursividad.  
  
 Para resolver este error, no defina macros ni propiedades en los términos en los que las macros suelen definirse.