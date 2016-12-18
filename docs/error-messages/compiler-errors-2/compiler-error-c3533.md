---
title: "Error del compilador C3533 | Microsoft Docs"
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
  - "C3533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3533"
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"tipo": un parámetro no puede tener un tipo que contiene "auto"  
  
 Un parámetro de método o plantilla no se puede declarar con la palabra clave `auto` si está activada la opción predeterminada del compilador [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md).  
  
### Para corregir este error  
  
1.  Quite la palabra clave `auto` de la declaración de parámetros.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque se declara un parámetro de función con la palabra clave `auto` y se compila con **\/Zc:auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque se declara un parámetro de plantilla con la palabra clave `auto` y se compila con **\/Zc:auto**.  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(Deducir tipo de variable\)](../../build/reference/zc-auto-deduce-variable-type.md)