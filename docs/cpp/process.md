---
title: "proceso | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Process"
  - "process_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], proceso"
  - "process __declspec (palabra clave)"
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# proceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso.  Se usa principalmente cuando se compila con **\/clr:pure**, ya que en **\/clr:pure** las variables globales y estáticas son por dominio de aplicación, de forma predeterminada.  Cuando se compila con **\/clr**, las variables globales y estáticas son por proceso de forma predeterminada \(no tiene que usar `__declspec(process)`\).  
  
 Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo se pueden marcar con `__declspec(process)`.  
  
 Al compilar con **\/clr:pure**, las variables marcadas como por proceso también se deben declarar como `const`.  De esta manera se garantiza que las variables por proceso no cambian en un dominio de aplicación, lo que puede generar resultados inesperados en otro dominio de aplicación.  El uso previsto principal de `__declspec(process)` es habilitar la inicialización en tiempo de compilación de una variable global, una variable miembro estática o una variable local estática en **\/clr:pure**.  
  
 `process` solo es válido cuando se compila con [\/clr](../build/reference/clr-common-language-runtime-compilation.md) o **\/clr:pure** y no es válido cuando se compila con **\/clr:safe**.  
  
 Si desea que cada dominio de aplicación tenga su propia copia de una variable global, utilice [appdomain](../cpp/appdomain.md).  
  
 Para obtener más información, vea [Dominios de aplicación y Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md).  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)