---
title: "Advertencia del compilador (nivel 3) C4073 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4073"
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

inicializadores situados en el área de inicialización de bibliotecas  
  
 Sólo los programadores de bibliotecas de terceros fabricantes deberían utilizar el área de inicialización de bibliotecas, que se especifica con la directiva [\#pragma init\_seg](../../preprocessor/init-seg.md).  El código siguiente genera el error C4073:  
  
```  
// C4073.cpp  
// compile with: /W3  
#pragma init_seg(lib)   // C4073  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```