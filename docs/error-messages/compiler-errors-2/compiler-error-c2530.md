---
title: "Error del compilador C2530 | Microsoft Docs"
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
  - "C2530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2530"
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : se deben inicializar las referencias  
  
 Es necesario inicializar una referencia en el momento de declararla, a menos que ya se haya declarado:  
  
-   Con la palabra clave [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   Como miembro de una clase, estructura o unión \(y se ha inicializado en el constructor\).  
  
-   Como parámetro en una declaración o definición de función.  
  
-   Como tipo de valor devuelto de una función.  
  
 El código siguiente genera el error C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```