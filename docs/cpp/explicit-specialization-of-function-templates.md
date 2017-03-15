---
title: "Especializaci&#243;n expl&#237;cita de las plantillas de funci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "declarar funciones, especialización de plantilla de función"
  - "especialización explícita de plantillas de función"
  - "plantillas de función, especialización"
  - "reemplazar, funciones"
  - "especialización de plantillas de función"
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Especializaci&#243;n expl&#237;cita de las plantillas de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con una plantilla de función, puede definir un comportamiento especial para un tipo específico si proporciona una especialización explícita \(reemplazo\) de la plantilla de función de ese tipo.  Por ejemplo:  
  
```  
template<> void MySwap(double a, double b);  
```  
  
 Esta declaración permite definir una función diferente para las variables de tipo **double**.  Al igual que en las funciones que no son de plantilla, se aplican las conversiones de tipo estándar \(por ejemplo, promover una variable de tipo **float** a tipo **double**\).  
  
## Ejemplo  
  
```  
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## Vea también  
 [Plantillas de función](../cpp/function-templates.md)