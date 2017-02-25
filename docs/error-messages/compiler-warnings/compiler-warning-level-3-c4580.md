---
title: "Advertencia del compilador (nivel 3) C4580 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4580"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4580"
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 3) C4580
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[attribute\] está desusado; especifique en su lugar System::Attribute o Platform::Metadata como clase base  
  
 [attribute](../../windows/attribute.md) ya no es la sintaxis recomendada para crear atributos definidos por el usuario.  Para obtener más información, vea [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  Para el código CLR, derive los atributos de [System::Attribute](assetId:///System::Attribute?qualifyHint=False&autoUpgrade=True).  Para el código Windows en tiempo de ejecución, derive los atributos de `Platform::Metadata`.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3454 y se muestra cómo corregirlo:  
  
```  
// C4580.cpp  
// compile with: /W3 /c /clr  
[attribute]   // C4580  
public ref class Attr {  
public:  
   int m_t;  
};  
  
public ref class Attr2 : System::Attribute {  
public:  
   int m_t;  
};  
```