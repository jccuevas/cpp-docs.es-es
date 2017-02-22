---
title: "Error del compilador C3638 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3638"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3638"
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3638
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : los operadores de conversión boxing y unboxing estándar no se pueden definir de nuevo  
  
 El compilador define un operador de conversión para que cada clase administrada admita la conversión boxing implícita.  No se puede volver a definir este operador.  
  
 Para obtener más información, vea [Conversión boxing implícita](../../windows/boxing-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3638:  
  
```  
// C3638.cpp  
// compile with: /clr  
value struct V {  
   V(){}  
   static operator V^(V);   // C3638  
};  
  
int main() {  
   V myV;  
   V ^ pmyV = myV;   // operator supports implicit boxing  
}  
```