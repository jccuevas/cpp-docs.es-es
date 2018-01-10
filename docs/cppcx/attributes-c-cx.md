---
title: Atributos (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dcd3818d21b644211891ae4779a6b9bf5074e6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-ccx"></a>Atributos (C++/CX)
Un atributo es un tipo especial de clase ref que se puede anteponer entre corchetes a tipos de Windows en tiempo de ejecución y métodos para especificar determinados comportamientos en la creación de metadatos. Varios atributos predefinidos, por ejemplo, [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx), se suelen usar en C++ / código CX. En este ejemplo se muestra cómo se aplica el atributo a una clase:  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Atributos personalizados  
 También puedes definir atributos personalizados. Atributos personalizados deben cumplir estas reglas en tiempo de ejecución de Windows:  
  
-   Los atributos personalizados solo pueden contener campos públicos.  
  
-   Los campos de atributos personalizados se pueden inicializar cuando el atributo se aplica a una clase.  
  
-   Un campo puede ser de uno de estos tipos:  
  
    -   int32 (int)  
  
    -   uint32 (int sin signo)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   clase de enumeración pública (incluye enumeraciones definidas por el usuario)  
  
 En el ejemplo siguiente se muestra cómo definir un atributo personalizado y e inicializarlo después cuando lo utilices.  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)