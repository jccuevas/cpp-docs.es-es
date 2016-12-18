---
title: "Error del compilador C3290 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3290"
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': una propiedad trivial no puede tener tipo de referencia  
  
 Se ha declarado incorrectamente una propiedad. Cuando se declara una propiedad trivial, el compilador crea una variable que actualizará la propiedad y no es posible tener una variable de referencia de seguimiento en una clase.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md) y [Operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3290.  
  
```  
// C3290.cpp // compile with: /clr /c ref struct R {}; ref struct X { R^ mr; property R % y;   // C3290 property R ^ x;   // OK // OK property R% prop { R% get() { return *mr; } void set(R%) {} } }; int main() { X x; R% xp = x.prop; }  
```