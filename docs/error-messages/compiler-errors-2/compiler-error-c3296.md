---
title: "Error del compilador C3296 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3296"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3296"
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3296
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'propiedad': ya existe una propiedad con este nombre.  
  
 El compilador encontró más de una propiedad con el mismo nombre. Cada propiedad de un tipo debe tener un nombre único.  
  
 Para obtener más información, consulta [propiedad](../../windows/property-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3296.  
  
```  
// C3296.cpp // compile with: /clr /c using namespace System; ref class R { public: property int MyProp[int] { int get(int); } property String^ MyProp[int] { void set(int, String^); }   // C3296 };  
```