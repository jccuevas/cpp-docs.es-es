---
title: "Conversi&#243;n boxing (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# Conversi&#243;n boxing (C++/CX)
*Boxing* es el ajuste de una variable de tipo de valor como [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) \(o un tipo escalar fundamental como `int`\) en una clase ref cuando la variable se pasa a un método que toma [Platform::Object^](../cppcx/platform-object-class.md) como tipo de entrada.  
  
## Pasar un tipo de valor a un parámetro de tipo Object^  
 Aunque no tengas que aplicar conversión boxing de forma explícita a una variable para pasarla a un parámetro de método de tipo [Platform::Object^](../cppcx/platform-object-class.md), tienes que volver a convertir de forma explícita al tipo original cuando recuperes valores a los que se ha aplicado conversión boxing previamente.  
  
 [!code-cpp[cx_boxing#01](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.cpp#01)]  
  
### Usar Platform::IBox\<T\> para admitir tipos de valor que aceptan valores NULL  
 C\# y Visual Basic admiten el concepto de tipos de valor que aceptan valores NULL. En [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], puedes utilizar el tipo `Platform::IBox<T>` para exponer métodos públicos que admiten parámetros de tipo de valor que aceptan valores NULL. En el siguiente ejemplo se muestra un método público de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] que devuelve NULL cuando un llamador de C\# pasa NULL para uno de los argumentos.  
  
 [!code-cpp[cx_boxing#02](../snippets/cpp/VS_Snippets_Misc/cx_boxing/cpp/class1.h#02)]  
  
 En un cliente XAML de C\#, puedes usarlo de este modo:  
  
```  
  
// C# client code BoxingDemo.Class1 obj = new BoxingDemo.Class1(); int? a = null; int? b = 5; var result = obj.Multiply(a,b); //result = null  
  
```  
  
## Vea también  
 [Sistema de tipos \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Convertir \(C\+\+\/CX\)](../cppcx/casting-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)