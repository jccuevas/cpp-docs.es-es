---
title: "Usar el control de excepciones estructurado con C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, en combinación con SEH"
  - "control estructurado de excepciones, con control de excepciones de C++"
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar el control de excepciones estructurado con C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control de excepciones estructurado descrito en estos artículos funciona con archivos de código fuente de C y C\+\+.  Sin embargo, no está diseñado específicamente para C\+\+ y no se recomienda.  Para asegurarse de que el código será más portable, use el control de excepciones de C\+\+.  Además, el mecanismo de control de excepciones de C\+\+ es más flexible, ya que puede controlar excepciones de cualquier tipo.  
  
 Microsoft C\+\+ admite el modelo de control de excepciones de C\+\+, basado en el estándar ANSI C\+\+.  Este mecanismo controla automáticamente la destrucción de objetos locales durante el desenredo de la pila.  Si está escribiendo código de C\+\+ con tolerancia a errores y desea implementar el control de excepciones, se recomienda encarecidamente utilizar el control de excepciones de C\+\+, en lugar del control de excepciones estructurado. \(Tenga en cuenta que mientras que el compilador de C\+\+ admite construcciones de control de excepciones estructurado como se describe en estos artículos, el compilador de C estándar no admite la sintaxis de control de excepciones de C\+\+\). Para obtener información detallada sobre el control de excepciones de C\+\+, vea [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md) y el *manual de referencia de C\+\+ con anotaciones* de Margaret Ellis y Bjarne Stroustrup.  
  
## Vea también  
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)