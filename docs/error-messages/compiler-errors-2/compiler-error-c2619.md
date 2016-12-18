---
title: "Error del compilador C2619 | Microsoft Docs"
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
  - "C2619"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2619"
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2619
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier%$S': no se permite un miembro de datos estático en un struct o unión anónimo  
  
 Se declara `static` un miembro anónimo de un struct o unión.  
  
 El ejemplo siguiente genera el error C2619 y muestra cómo corregirlo eliminando la palabra clave static.  
  
```  
// C2619.cpp  
int main() {  
   union { static int j; };  // C2619  
   union { int j; };  // OK  
}  
```