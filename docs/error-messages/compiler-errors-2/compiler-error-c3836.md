---
title: "Error del compilador C3836 | Microsoft Docs"
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
  - "C3836"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3836"
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3836
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite que el constructor estático tenga una lista de inicializadores de miembro  
  
 Una clase administrada no puede tener un constructor estático que también tenga una lista de inicialización de miembros.  Los constructores de clases estáticas son llamados por Common Language Runtime para realizar la inicialización de clase, inicializando los miembros de datos estáticos.  
  
 El código siguiente genera el error C3836:  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
 El código siguiente genera el error C3836:  
  
```  
// C3836b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```