---
title: "Advertencia del compilador (nivel 1) C4530 | Microsoft Docs"
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
  - "C4530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4530"
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se ha utilizado el controlador de excepciones de C\+\+, pero la semántica de desenredo no está habilitada.Especifique \/EHsc  
  
 Se ha utilizado el control de excepciones de C\+\+, pero no se seleccionó la opción [\/EHsc](../../build/reference/eh-exception-handling-model.md).  
  
 Cuando no está habilitada la opción \/EHsc, un objeto que posea almacenamiento automático en el marco, entre la función que realiza la captura y la función que produce la captura, no se destruirá.  Sin embargo, un objeto con almacenamiento automático creado en un bloque **try** o **catch** sí se destruirá.  
  
 El código siguiente genera el error C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 Compile el ejemplo con \/EHsc para resolver la advertencia.