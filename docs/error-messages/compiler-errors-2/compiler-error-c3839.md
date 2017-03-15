---
title: "Error del compilador C3839 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3839"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3839"
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3839
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede cambiar la alineación en un tipo administrado o WinRT  
  
 La alineación de variables en tipos administrados o de Windows en tiempo de ejecución está controlada por CLR o Windows en tiempo de ejecución y no puede modificarse con [align](../../cpp/align-cpp.md).  
  
 El ejemplo siguiente genera el error C3839:  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
  
```