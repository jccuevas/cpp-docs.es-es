---
title: "Error de las herramientas del vinculador LNK2033 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2033"
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Error de las herramientas del vinculador LNK2033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo \(token\) de typeref sin resolver para 'tipo'  
  
 Un tipo no tiene una definición en metadatos de MSIL.  
  
 El error LNK2033 puede producirse cuando se compila con **\/clr:safe** y sólo hay una declaración adelantada de un tipo en un módulo MSIL, al que se hace referencia en dicho módulo.  
  
 El tipo debe definirse bajo **\/clr:safe**.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK2033.  
  
```  
// LNK2033.cpp  
// compile with: /clr:safe  
// LNK2033 expected  
ref class A;  
ref class B {};  
  
int main() {  
   A ^ aa = nullptr;  
   B ^ bb = nullptr;   // OK  
};  
```