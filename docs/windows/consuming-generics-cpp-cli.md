---
title: "Consumir gen&#233;ricos (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "genéricos [C++], utilizar desde lenguajes .NET"
ms.assetid: e6330ef5-e907-432e-b527-7a22f5899639
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Consumir gen&#233;ricos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los genéricos creados en un lenguaje.NET se pueden utilizar en otros lenguajes.NET.  A diferencia de las plantillas, un genérico en un ensamblado compilado todavía sigue siendo genérico.  Así, se puede crear una instancia del tipo genérico en un ensamblado diferente e incluso en otro idioma que el ensamblado en el que se ha definido el tipo genérico.  
  
## Comentarios  
 Para obtener más información, vea:  
  
-   [Introducción a los genéricos](../Topic/Introduction%20to%20Generics%20\(C%23%20Programming%20Guide\).md)  
  
-   [Tipos genéricos en Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)  
  
## Ejemplo  
  
### Descripción  
 Este ejemplo muestra una clase genérica definida en C\#.  
  
### Código  
  
```  
// consuming_generics_from_other_NET_languages.cs  
// compile with: /target:library  
// a C# program  
public class CircularList<ItemType> {  
   class ListNode    {  
      public ItemType m_item;  
      public ListNode next;  
      public ListNode(ItemType item) {  
         m_item = item;  
      }  
   }  
  
   ListNode first, last;  
  
   public CircularList() {}  
  
   public void Add(ItemType item) {  
      ListNode newnode = new ListNode(item);  
      if (first == null) {  
         first = last = newnode;  
         first.next = newnode;  
         last.next = first;  
      }  
      else {  
         newnode.next = first;  
         first = newnode;  
         last.next = first;  
      }   
   }  
  
   public void Remove(ItemType item) {  
      ListNode iter = first;  
      if (first.m_item.Equals( item )) {  
         first =   
         last.next = first.next;  
      }  
      for ( ; iter != last ; iter = iter.next )  
         if (iter.next.m_item.Equals( item )) {  
              if (iter.next == last)  
                  last = iter;  
              iter.next = iter.next.next;  
              return;  
          }  
   }  
  
   public void PrintAll() {  
      ListNode iter = first;  
      do {  
         System.Console.WriteLine( iter.m_item );  
         iter = iter.next;  
      } while (iter != last);  
   }  
}  
```  
  
## Ejemplo  
  
### Descripción  
 Este ejemplo utiliza el ensamblado creado en C\#.  
  
### Código  
  
```  
// consuming_generics_from_other_NET_languages_2.cpp  
// compile with: /clr  
#using <consuming_generics_from_other_NET_languages.dll>  
using namespace System;  
class NativeClass {};  
ref class MgdClass {};  
  
int main() {  
   CircularList<int>^ circ1 = gcnew CircularList<int>();  
   CircularList<MgdClass^>^ circ2 = gcnew CircularList<MgdClass^>();  
  
   for (int i = 0 ; i < 100 ; i += 10)  
      circ1->Add(i);  
   circ1->Remove(50);  
   circ1->PrintAll();  
}  
```  
  
### Resultados  
  
```  
90  
80  
70  
60  
40  
30  
20  
10  
```  
  
## Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)