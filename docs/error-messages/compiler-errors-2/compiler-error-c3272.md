---
title: "Error del compilador C3272 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3272"
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': el símbolo requiere FieldOffset, ya que es miembro de tipo nombredetipo definido con StructLayout\(LayoutKind::Explicit\)  
  
 Cuando [StructLayout](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic) `Explicit` está activo, los campos deben estar marcados con [FieldOffset](frlrfSystemRuntimeInteropServicesFieldOffsetAttributeClassTopic).  
  
 El ejemplo siguiente genera la advertencia C3272:  
  
```  
// C3272_2.cpp // compile with: /clr /c using namespace System; using namespace System::Runtime::InteropServices; [StructLayout(LayoutKind::Explicit)] ref struct X { int data_;   // C3272 // try the following line instead // [FieldOffset(0)] int data_; };  
```  
  
 El ejemplo siguiente genera la advertencia C3272:  
  
```  
// C3272.cpp // compile with: /clr:oldSyntax /LD #using <mscorlib.dll> using namespace System; using namespace System::Runtime::InteropServices; [StructLayout(LayoutKind::Explicit)] __gc struct X { int data_;   // C3272 // try the following line instead // [FieldOffset(0)] int data_; };  
```