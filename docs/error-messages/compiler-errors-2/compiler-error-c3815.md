---
title: "Error del compilador C3815 | Microsoft Docs"
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
  - "C3815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3815"
ms.assetid: c5a3b404-6341-4fd3-92af-152b404c4dde
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el tipo de valor devuelto del método 'get\_accessor' debe coincidir con el tipo del último parámetro de un establecedor  
  
 Al declarar [propiedades](../../misc/property.md), el valor devuelto del método `get_accessor` debe coincidir con el último parámetro de la declaración del método de descriptor de acceso Set.  
  
 El error C3815 solo se puede reproducir usando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3815:  
  
```  
// C3815.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc class X  
{  
public:  
   __property char get_N()  
   // try the following line instead  
   // __property int get_N()  
   {  
      return m_val;  
   }  
  
   __property void set_N( int val)  
   {  
      m_val = val;  
   }  
  
private:  
   int m_val;  
};   // C3815  
```  
  
 En el ejemplo siguiente se muestra cómo sobrecargar las propiedades de manera que el tipo de valor devuelto del método Get no coincida con el último parámetro del método Set.  
  
```  
// C3815b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
public __gc class MyClass {  
public:  
// 1st property:  
   __property System::Int32 get_p1();  
   __property void set_p1(System::Int32 i);  
  
// 2nd property (only setter):  
   __property void set_p1(System::Int32* i);  
  
};  
```