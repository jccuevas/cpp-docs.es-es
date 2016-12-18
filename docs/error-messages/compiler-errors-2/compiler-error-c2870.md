---
title: "Error del compilador C2870 | Microsoft Docs"
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
  - "C2870"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2870"
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2870
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : una definición de espacio de nombres debe aparecer en el ámbito de archivo o directamente dentro de otra definición de espacio de nombres  
  
 Se definió incorrectamente el espacio de nombres `name`.  Los espacios de nombres se deben definir en el ámbito de archivo \(fuera de todos los bloques y clases\) o de forma inmediata dentro de otro espacio de nombres.  
  
 El código siguiente genera el error C2870:  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```