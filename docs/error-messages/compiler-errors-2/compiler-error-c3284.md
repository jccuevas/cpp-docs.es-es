---
title: "Error del compilador C3284 | Microsoft Docs"
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
  - "C3824"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3284"
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3284
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las restricciones del parámetro genérico 'parámetro' de la función 'función' deben coincidir con las restricciones correspondientes al parámetro genérico 'parámetro' de la función 'función'.  
  
 Una función genérica virtual debe usar las mismas restricciones que una función virtual con el mismo nombre y conjunto de argumentos de la clase base.  
  
 El ejemplo siguiente genera la advertencia C3284:  
  
```  
// C3284.cpp // compile with: /clr /c // C3284 expected public interface class IGettable { int Get(); }; public interface class B { generic<typename T> where T : IGettable virtual int mf(T t); }; public ref class D : public B { public: generic<typename T> // Uncomment the following line to resolve. // where T : IGettable virtual int mf(T t) { return 4; } };  
```