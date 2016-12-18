---
title: "Advertencia del compilador (nivel 1) C4692 | Microsoft Docs"
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
  - "C4692"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4692"
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4692
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo\_nativo'  
  
 Un tipo visible fuera del ensamblado incluye una función miembro cuya firma contiene un tipo nativo no visible fuera del ensamblado.  Por consiguiente, no se debería llamar a la función miembro si se crean instancias de su tipo fuera del ensamblado.  
  
 Para obtener más información, vea [Visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4692.  
  
```  
// C4692.cpp  
// compile with: /W1 /c /clr  
#pragma warning(default:4692)  
class Private_Native_Class {};  
public class Public_Native_Class {};  
public ref class Public_Ref_Class {  
public:  
   void Test(Private_Native_Class *) {}   // C4692  
   void Test2(Public_Native_Class *) {}   // OK  
};  
```