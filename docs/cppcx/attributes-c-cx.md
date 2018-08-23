---
title: Atributos (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7db8d6c527842cd3784623002fba001a4174c1fc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601143"
---
# <a name="attributes-ccx"></a>Atributos (C++/CX)
Un atributo es un tipo especial de clase ref que se puede anteponer entre corchetes a los tipos de Windows en tiempo de ejecución y métodos para especificar determinados comportamientos en la creación de metadatos. Varios atributos predefinidos, por ejemplo, [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx): se usan normalmente en C++ / c++ / código CX. En este ejemplo se muestra cómo se aplica el atributo a una clase:  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Atributos personalizados  
 También puedes definir atributos personalizados. Los atributos personalizados deben cumplir estas reglas de Windows en tiempo de ejecución:  
  
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