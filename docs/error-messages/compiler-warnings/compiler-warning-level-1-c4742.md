---
title: "Advertencia del compilador (nivel 1) C4742 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4742"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4742"
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4742
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' tiene una alineación diferente en 'archivo1' y 'archivo2': número y número  
  
 Una variable externa definida o a la que se hizo referencia en dos archivos tiene diferente alineación en dichos archivos.  Esta advertencia se produce cuando el compilador encuentra que `__alignof` para la variable en *file1* diferencia de `__alignof` para la variable en *file2*.  Esto puede ser debido al uso de tipos incompatibles cuando se declaran variables en archivos diferentes o al uso de `#pragma pack` no correspondiente en archivos diferentes.  
  
 Para solucionarlo, utilice la misma definición de tipo o denomine las variables con nombres diferentes.  
  
 Para obtener más información, vea [pack](../../preprocessor/pack.md) y [\_\_alignof \(Operador\)](../../cpp/alignof-operator.md).  
  
## Ejemplo  
 Éste es el primer archivo que define el tipo.  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4742.  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```