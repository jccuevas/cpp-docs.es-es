---
title: "Error de las herramientas del vinculador LNK2028 | Microsoft Docs"
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
  - "LNK2028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2028"
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se hace referencia a "exported\_function" \(decorated\_name\) en función "function\_containing\_function\_call \(decorated\_name\)"  
  
 Cuando importe una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas son distintas en las compilaciones puras y nativas.  
  
## Ejemplo  
 Este ejemplo de código genera un componente con una función nativa exportada, cuya convención de llamada es implícitamente [\_\_cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente crea un cliente puro que utiliza la función nativa.  Sin embargo, la convención de llamada bajo **\/clr:pure** es [\_\_clrcall](../../cpp/clrcall.md).  El ejemplo siguiente genera el error LNK2028.  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```