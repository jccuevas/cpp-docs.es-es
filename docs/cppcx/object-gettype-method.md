---
title: "Object::GetType (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetType"
ms.assetid: f633d71a-ff80-49f9-931d-189c00b1f6c5
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetType (M&#233;todo)
Devuelve un objeto [Platform::Type](../cppcx/platform-type-class.md) que describe el tipo en tiempo de ejecución de un objeto.  
  
## Sintaxis  
  
```vb  
Object::GetType()  
```  
  
```csharp  
  
```  
  
## Valor de propiedad y valor devuelto  
 Objeto [Platform::Type](../cppcx/platform-type-class.md) que describe el tipo en tiempo de ejecución del objeto.  
  
## Comentarios  
 Se puede usar el método estático [Type::GetTypeCode \(Método\)](../cppcx/type-gettypecode-method.md) para obtener un valor de [Platform::TypeCode \(Enumeración\)](../cppcx/platform-typecode-enumeration.md) que represente el tipo actual. Esto es especialmente útil para los tipos integrados. El código de tipo de cualquier clase ref además de [Platform::String](../cppcx/platform-string-class.md) es Object \(1\).  
  
 La clase [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) se usa en las API de Windows como una manera independiente del lenguaje de pasar información de tipos entre los componentes y aplicaciones Windows. T[Platform::Type \(Clase\)](../cppcx/platform-type-class.md) tiene operadores para la conversión entre `Type` y `TypeName`.  
  
 Utiliza el operador [typeid](http://msdn.microsoft.com/library/e9706cae-e7c4-4d6d-b474-646d73df3e70) para devolver un objeto de `Platform::Type` para un nombre de clase, por ejemplo, al navegar entre páginas XAML:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## Vea también  
 [Platform::Type \(Clase\)](../cppcx/platform-type-class.md)   
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)   
 [Sistema de tipos](../cppcx/type-system-c-cx.md)