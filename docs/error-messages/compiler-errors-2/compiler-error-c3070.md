---
title: "Error del compilador C3070 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3070"
ms.assetid: ac88584d-40a6-4176-90f3-2371c3c935f2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'property': la propiedad no tiene un método 'set'  
  
 No se definió el método de descriptor de acceso set de una propiedad. Para obtener más información, consulta [propiedad](../../windows/property-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera la advertencia C3070:  
  
```  
// C3070.cpp // compile with: /clr ref class R { public: R(int size) { m_data = gcnew array<int>(size); } property int % MyProp[int] { int% get(int index) { return m_data[index]; } } property int % MyProp2[int] { int% get(int index) { return m_data[index]; } void set(int index, int % value) {} } property const int % MyProp3[int] { const int% get(int index) { return m_data[index]; } void set(int index, const int % value) {} } private: array<int>^ m_data; }; int main() { R^ r = gcnew R(10); r->MyProp[4] = 4;   // C3070 int value = 4; r->MyProp2[4] = value;   // OK r->MyProp3[4] = 4;   // OK }  
```