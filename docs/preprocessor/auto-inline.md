---
title: "auto_inline | Microsoft Docs"
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
  - "auto_inline_CPP"
  - "vc-pragma.auto_inline"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "auto_inline (pragma)"
  - "pragma (directivas), auto_inline"
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# auto_inline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Excluye cualquier función definida dentro del intervalo donde se especifica **off** de considerarse como candidato a la expansión en línea automática.  
  
## Sintaxis  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## Comentarios  
 Para utilizar la pragma **auto\_inline**, colóquela delante e inmediatamente después \(no dentro\) de una definición de función.  La pragma surte efecto en cuanto aparece en la primera definición de función.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)