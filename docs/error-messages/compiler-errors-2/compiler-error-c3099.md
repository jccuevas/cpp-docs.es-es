---
title: "Compiler Error C3099 | Microsoft Docs"
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
  - "C3099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3099"
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword': use \[System::AttributeUsageAttribute\] para atributos administrados; use \[Windows::Foundation::Metadata::AttributeUsageAttribute\] para atributos WinRT  
  
 Use <xref:System.AttributeUsageAttribute> para declarar atributos **\/clr**.  Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.  
  
 Para obtener más información sobre atributos \/CLR, vea [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  Para atributos admitidos en Windows Runtime, vea [Espacio de nombres Windows.Foundation.Metadata](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3099 y muestra cómo corregirlo:  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```