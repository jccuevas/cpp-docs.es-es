---
title: "Error del compilador C3813 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3813"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3813"
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una declaración de propiedad solo puede aparecer en la definición de un tipo WinRT o administrado  
  
 Una [property](../../misc/property.md) solo puede declararse dentro de un tipo Windows en tiempo de ejecución o administrado.  Los tipos nativos no admiten la palabra clave `property`.  
  
 En el ejemplo siguiente se genera el error C3813 y se muestra cómo corregirlo:  
  
```  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```