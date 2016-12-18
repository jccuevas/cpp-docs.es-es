---
title: "Compiler Error C3450 | Microsoft Docs"
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
  - "C3450"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3450"
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3450
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': no es un atributo; no puede especificar \[System::AttributeUsageAttribute\] ni \[Windows::Foundation::Metadata::AttributeUsageAttribute\]  
  
 Un atributo administrado definido por el usuario debe heredar de <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>.  Se debe definir un atributo de tiempo de ejecución de Windows en el espacio de nombres `Windows::Foundation::Metadata`.  
  
 Para más información, vea [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3450 y muestra cómo corregirlo.  
  
```  
// C3450.cpp  
// compile with: /clr  
// C3450 expected  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass {  
   AtClass(Type ^) {}  
};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass2 {  
   AtClass2() {}  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
// Delete the following line to resolve.  
ref class B {};  
// Uncomment the following line to resolve.  
// ref class B : Attribute {};  
```