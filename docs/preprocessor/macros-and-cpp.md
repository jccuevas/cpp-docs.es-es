---
title: "Macros y C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "macros"
  - "macros, C++"
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Macros y C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ proporciona nuevas capacidades que suplantan, algunas de ellas, a las proporcionadas por el preprocesador de ANSI C.  Estas nuevas capacidades mejoran la seguridad de tipos y la previsibilidad del lenguaje:  
  
-   En C\+\+, los objetos declarados como **const** se pueden utilizar en expresiones de constante.  Esto permite que los programas declaren constantes que tienen información de tipo y valor, y enumeraciones que se pueden ver simbólicamente con el depurador.  El uso de la directiva `#define` de preprocesador para definir constantes no es tan preciso.  No se asigna ningún almacenamiento para un objeto **const**, a menos que se encuentre en el programa una expresión que tome su dirección.  
  
-   La capacidad de función insertada de C\+\+ suplanta las macros de tipo de función.  Las ventajas de utilizar funciones insertadas respecto a macros son:  
  
    -   Seguridad de tipos.  Las funciones insertadas están sujetas a la misma comprobación de tipos que las funciones normales.  Las macros no tienen seguridad de tipos.  
  
    -   Se corrige el control de argumentos que tienen efectos secundarios.  Las funciones insertadas evalúan las expresiones proporcionadas como argumentos antes de escribir el cuerpo de la función.  Por lo tanto, no hay posibilidad de que una expresión con efectos secundarios no sea segura.  
  
 Para obtener más información sobre las funciones insertadas, vea [inline, \_\_inline, \_\_forceinline](../misc/inline-inline-forceinline.md).  
  
 Por compatibilidad con versiones anteriores, todos los servicios de preprocesador que existían en ANSI C y en las especificaciones anteriores de C\+\+ se conservan para Microsoft C\+\+.  
  
## Vea también  
 [Macros predefinidas](../preprocessor/predefined-macros.md)   
 [Macros](../preprocessor/macros-c-cpp.md)