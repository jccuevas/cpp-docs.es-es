---
title: "Enumeraciones (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 14
---
# Enumeraciones (C++/CX)
[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] admite la palabra clave `public enum class`, que es análoga a un objeto `scoped  enum` de C\+\+ estándar. Cuando utilices un enumerador que se declara mediante la palabra clave `public enum class`, debes usar el identificador de enumeración para determinar el ámbito de cada valor de enumerador.  
  
## Comentarios  
 Una `public enum class` que no tiene un especificador de acceso, como `public`, se trata como una [enumeración con ámbito](../Topic/Enumerations%20\(C++\).md) de C\+\+ estándar.  
  
 Una declaración de `public enum class` o de `public enum struct` puede tener un tipo subyacente de cualquier tipo entero aunque el propio [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] requiera que el tipo sea int32, o uint32 para una enumeración de marcas. La sintaxis siguiente describe las partes de un objeto `public enum class` o `public enum struct`. Para obtener más información, consulta [enum class](../Topic/enum%20class%20%20\(C++%20Component%20Extensions\).md).  
  
 En este ejemplo se muestra cómo definir una clase de enumeración pública:  
  
 [!code-cpp[cx_enums#01](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#01)]  
  
 En este ejemplo siguiente se muestra cómo usarla:  
  
 [!code-cpp[cx_enums#02](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#02)]  
  
## Ejemplos  
 En los ejemplos siguientes se muestra cómo declarar una enumeración:  
  
 [!code-cpp[cx_enums#03](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#03)]  
  
 En el ejemplo siguiente se muestra cómo convertirla a equivalentes numéricos y realizar comparaciones. Observa que el ámbito del uso del enumerador `One` lo determina el identificador de la enumeración `Enum1`, y el ámbito del enumerador `First` lo determina `Enum2`.  
  
 [!code-cpp[cx_enums#04](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#04)]  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)