---
title: "Platform::Type (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Type (Clase)"
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Type (Clase)
Contiene información en tiempo de ejecución sobre un tipo, en concreto, un nombre de cadena y un typecode. Se obtiene llamando al [método Object::GetType](../cppcx/object-gettype-method.md) en cualquier objeto o utilizando el operador [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) en un nombre de struct o clase.  
  
## Sintaxis  
  
```cpp  
public ref class Platform::Type :      Platform::Object,      Platform::Details::IEquatable,      Platform::Details::IPrintable  
```  
  
## Comentarios  
 La clase `Type` es útil en aplicaciones que deben dirigir el procesamiento mediante una instrucción `if` o `switch` que se bifurca en función del tipo en tiempo de ejecución de un objeto. El código de tipo que describe la categoría de un tipo se recupera utilizando la función miembro del [método Type::GetTypeCode](../cppcx/type-gettypecode-method.md).  
  
## Métodos públicos  
  
|||  
|-|-|  
|[Type::GetTypeCode \(Método\)](../cppcx/type-gettypecode-method.md)|Devuelve un valor de [enumeración Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) para el objeto.|  
  
## Propiedades públicas  
  
|||  
|-|-|  
|[Type::FullName \(Propiedad\)](../cppcx/type-fullname-property.md)|Devuelve una [clase Platform::String](../cppcx/platform-string-class.md)^ que representa el nombre completo del tipo y usa . \(punto\) como separador, no :: \(dos puntos\); por ejemplo, “MyNamespace.MyClass”.|  
  
## Operadores de conversión  
  
|||  
|-|-|  
|[operador Type^](../cppcx/operator-subtracttype-hat.md)|Permite la conversión de `Windows::UI::Xaml::Interop::TypeName` a `Platform::Type`.|  
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|Permite la conversión de `Platform::Type` a `Windows::UI::Xaml::Interop::TypeName`.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)