---
title: "Error del compilador C3893 | Microsoft Docs"
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
  - "C3893"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3893"
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3893
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : el uso del valor L del miembro de datos initonly solamente se permite en un constructor de instancia de clase 'nombre\_tipo'  
  
 Las direcciones de los miembros de datos [initonly](../../dotnet/initonly-cpp-cli.md) estáticos solo pueden tomarse en un constructor estático.  
  
 Las direcciones de los miembros de datos initonly \(no estáticos\) de instancias sólo pueden tomarse en constructores \(no estáticos\) de instancias.  
  
 El código siguiente genera el error C3893:  
  
```  
// C3893.cpp  
// compile with: /clr  
ref struct Y1 {  
   Y1() : data_var(0) {  
      int% i = data_var;   // OK  
   }  
   initonly int data_var;  
};  
  
int main(){  
   Y1^ y= gcnew Y1;  
   int% i = y->data_var;   // C3893  
}  
```