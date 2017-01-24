---
title: "Error del compilador C2299 | Microsoft Docs"
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
  - "C2299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2299"
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : cambio de comportamiento: una especialización explícita no puede ser un constructor de copias ni un operador de asignación de copia  
  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: versiones anteriores de Visual C\+\+ permitían la especialización explícita de un constructor de copias o de un operador de asignación de copia.  
  
 Para solucionar el error C2299, no cree una función de plantilla de un constructor de copias u operador de asignación de copia; haga una función que no sea de plantilla y que admita un tipo de clase.   El código que llama al constructor de copias u operador de asignación especificando explícitamente los argumentos de plantilla debe quitar dichos argumentos.  
  
 El código siguiente genera el error C2299:  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```