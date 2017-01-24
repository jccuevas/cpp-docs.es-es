---
title: "C&#243;mo: Consumir un indizador de C# (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++, indizadores"
  - "indizadores, utilizar en C#"
ms.assetid: 5a11850c-a1a2-4a0a-b95e-f6dc5a87f439
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Consumir un indizador de C# (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ no contiene indizadores; tiene propiedades indizadas.  Para consumir un indizador de C\#, obtenga acceso al indizador si se tratara de una propiedad indizada.  
  
 Para obtener más información sobre indizadores, vea:  
  
-   [Indizadores](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md)  
  
-   [Cómo: Usar las propiedades indizadas](../misc/how-to-use-indexed-properties.md)  
  
## Ejemplo  
 El siguiente programa de C\# define un indizador.  
  
```  
// consume_cs_indexers.cs  
// compile with: /target:library  
using System;  
public class IndexerClass {  
   private int [] myArray = new int[100];   
   public int this [int index] {   // Indexer declaration  
      get {  
         // Check the index limits.  
         if (index < 0 || index >= 100)  
            return 0;  
         else  
            return myArray[index];  
      }  
      set {  
         if (!(index < 0 || index >= 100))  
            myArray[index] = value;  
      }  
   }  
}  
/*  
// code to consume the indexer  
public class MainClass {  
   public static void Main() {  
      IndexerClass b = new IndexerClass();  
  
      // Call indexer to initialize elements 3 and 5  
      b[3] = 256;  
      b[5] = 1024;  
      for (int i = 0 ; i <= 10 ; i++)   
         Console.WriteLine("Element #{0} = {1}", i, b[i]);  
   }  
}  
*/  
```  
  
## Ejemplo  
 Este programa de Visual C\+\+ consume el indizador.  
  
```  
// consume_cs_indexers_2.cpp  
// compile with: /clr  
#using "consume_cs_indexers.dll"  
using namespace System;  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->default[0] = 21;  
   for (int i = 0 ; i <= 10 ; i++)  
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);  
}  
```  
  
  **Elemento \#0 \= 21**  
**Elemento \#1 \= 0**  
**Elemento \#2 \= 0**  
**Elemento \#3 \= 0**  
**Elemento \#4 \= 0**  
**Elemento \#5 \= 0**  
**Elemento \#6 \= 0**  
**Elemento \#7 \= 0**  
**Elemento \#8 \= 0**  
**Elemento \#9 \= 0**  
**Elemento \#10 \= 0**   
## Vea también  
 [Interoperabilidad con otros lenguajes de .NET](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)