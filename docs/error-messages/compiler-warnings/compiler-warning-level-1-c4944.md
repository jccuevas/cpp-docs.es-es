---
title: "Advertencia del compilador (nivel 1) C4944 | Microsoft Docs"
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
  - "C4944"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4944"
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4944
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': no se puede importar un símbolo desde 'assembly1': ya que 'symbol' ya existe en el ámbito actual.  
  
 Se definió un símbolo en un archivo de código fuente y, a continuación, una instrucción \#using hizo referencia a un ensamblado que también define el símbolo. Se ha ignorado el símbolo en el ensamblado.  
  
## Ejemplo  
 En el ejemplo siguiente se crea un componente con un tipo llamado ClassA.  
  
```  
// C4944.cs // compile with: /target:library // C# source code to create a dll public class ClassA { public int i; }  
```  
  
## Ejemplo  
 Los ejemplos siguientes generan C4944.  
  
```  
// C4944b.cpp // compile with: /clr /W1 class ClassA { public: int u; }; #using "C4944.dll"   // C4944 ClassA also defined C4944.dll int main() { ClassA * x = new ClassA(); x->u = 9; System::Console::WriteLine(x->u); }  
```