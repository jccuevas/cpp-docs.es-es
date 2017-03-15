---
title: "Error del compilador C3451 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3451"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3451"
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Error del compilador C3451
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'atributo' : no se puede aplicar el atributo no administrado a 'tipo'  
  
 Un atributo de C\+\+ no se puede aplicar a un tipo CLR.  Para obtener más información, vea [C\+\+ Attributes Reference](../../windows/cpp-attributes-reference.md).  
  
 Para obtener más información, vea [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Este error también se puede producir como resultado del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: el atributo [uuid](../../windows/uuid-cpp-attributes.md) ya no está permitido en un atributo definido por el usuario que utilice programación CLR.  Utilice <xref:System.Runtime.InteropServices.GuidAttribute> en su lugar.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3451.  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```