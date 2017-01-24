---
title: "Error del compilador C3247 | Microsoft Docs"
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
  - "C3247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3247"
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class1': una coclase no puede heredar de otra coclase 'class2'  
  
 Una clase marcada con atributo [coclass](../../windows/coclass.md) no puede heredar de otra clase marcada con el atributo `coclass`.  
  
 El ejemplo siguiente genera la advertencia C3247:  
  
```  
// C3247.cpp [module(name="MyLib")]; [coclass] class a { }; [coclass] class b : public a {   // C3247 }; int main() { }  
```