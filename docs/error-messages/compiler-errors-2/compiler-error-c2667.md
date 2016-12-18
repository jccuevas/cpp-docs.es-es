---
title: "Error del compilador C2667 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2667"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2667"
ms.assetid: 3c91d9d1-18fa-4e0d-a9ba-984d38980ca3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2667
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : ninguna de las sobrecargas número tiene una conversión mejor  
  
 Una llamada a una función sobrecargada es ambigua y no se puede resolver.  
  
 La conversión requerida para hacer coincidir los parámetros reales de la llamada de la función a una de las funciones sobrecargadas debe ser estrictamente mejor que las conversiones requeridas por todas las demás funciones sobrecargadas.  
  
 Vea el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.