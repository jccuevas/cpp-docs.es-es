---
title: "Atributos (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Atributos (C++/CX)
Un atributo es un tipo especial de clase ref que se puede anteponer entre corchetes a los tipos y métodos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] para especificar determinados comportamientos en la creación de metadatos. Varios atributos predefinidos, por ejemplo, [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx), normalmente se usan en código [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]. En este ejemplo se muestra cómo se aplica el atributo a una clase:  
  
 [!code-cpp[cx_attributes#01](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#01)]  
  
## Atributos personalizados  
 También puedes definir atributos personalizados. Los atributos personalizados deben cumplir estas reglas de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]:  
  
-   Los atributos personalizados solo pueden contener campos públicos.  
  
-   Los campos de atributos personalizados se pueden inicializar cuando el atributo se aplica a una clase.  
  
-   Un campo puede ser de uno de estos tipos:  
  
    -   int32 \(int\)  
  
    -   uint32 \(int sin signo\)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   clase de enumeración pública \(incluye enumeraciones definidas por el usuario\)  
  
 En el ejemplo siguiente se muestra cómo definir un atributo personalizado y e inicializarlo después cuando lo utilices.  
  
 [!code-cpp[cx_attributes#02](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#02)]  
  
## Vea también  
 [Sistema de tipos \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)