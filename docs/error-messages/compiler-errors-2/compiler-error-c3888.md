---
title: "Error del compilador C3888 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3888"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3888"
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3888
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name': C\+\+\/CLI no admite la expresión const asociada con este miembro de datos literal  
  
 El miembro de datos *name* que se declara con la palabra clave [literal](../../windows/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.  
  
### Para corregir este error  
  
1.  Compruebe que el miembro de datos declarado literal es un tipo admitido.  
  
## Vea también  
 [literal](../../windows/literal-cpp-component-extensions.md)