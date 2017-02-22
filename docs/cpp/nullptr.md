---
title: "nullptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "nullptr_cpp"
  - "nullptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nullptr (palabra clave) [C++]"
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# nullptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa una constante de puntero null de tipo `std::nullptr_t`, que se puede convertir a cualquier tipo de puntero sin formato.  Aunque puede utilizar la palabra clave `nullptr` sin incluir ningún encabezado, si el código usa el tipo `std::nullptr_t`, debe definirlo incluyendo el encabezado `<cstddef>`.  
  
> [!NOTE]
>  La palabra clave `nullptr` también se define en C\+\+\/CLI para aplicaciones de código administrado y no es intercambiable con la palabra clave de C\+\+ del estándar ISO.  Si el código podría compilarse con la opción [\/clr](../build/reference/clr-common-language-runtime-compilation.md) del compilador, destinada a código administrado, use `__nullptr` en cualquier línea de código donde debe garantizar que el compilador usa la interpretación de C\+\+ nativa.  Para obtener más información, vea [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## Comentarios  
 Evite usar `NULL` o cero \(`0`\) como constante de puntero null; `nullptr` es menos vulnerable en caso de mal uso y funciona mejor en la mayoría de las situaciones.  Por ejemplo, dado `func(std::pair<const char *, double>)`, la llamada a `func(std::make_pair(NULL, 3.14))` produce un error del compilador.  La macro NULL se expande a `0`, de modo que la llamada `std::make_pair(0, 3.14)` devuelve `std::pair<int, double>`, que no se puede convertir al tipo de parámetro `std::pair<const char *, double>` de func\(\).  La llamada a `func(std::make_pair(nullptr, 3.14))` se compila correctamente porque `std::make_pair(nullptr, 3.14)` devuelve `std::pair<std::nullptr_t, double>`, que se puede convertir en `std::pair<const char *, double>`.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)