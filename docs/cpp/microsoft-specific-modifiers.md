---
title: "Modificadores espec&#237;ficos de Microsoft | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Modificadores espec&#237;ficos de Microsoft
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En esta sección se describen las extensiones específicas de Microsoft para C\+\+ en las áreas siguientes:  
  
-   [Direccionamiento de base](../cpp/based-addressing.md), la práctica de usar un puntero como base desde la que se pueden desplazar otros punteros  
  
-   [Convenciones de llamadas a función](../cpp/calling-conventions.md)  
  
-   Atributos extendidos de clase de almacenamiento declarados con la palabra clave [\_\_declspec](../cpp/declspec.md)  
  
-   Palabra clave [\_\_w64](../cpp/w64.md)  
  
 Muchas de las palabras clave específicas de Microsoft se pueden utilizar para modificar declaradores y formar tipos derivados.  Para obtener más información sobre los declaradores, vea [Declaradores](http://msdn.microsoft.com/es-es/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
### Palabras clave específicas de Microsoft  
  
|Palabra clave|Significado|¿Se usa para formar tipos derivados?|  
|-------------------|-----------------|------------------------------------------|  
|[\_\_based](../cpp/based-grammar.md)|El nombre que sigue declara un desplazamiento de 32 bits con respecto a la base de 32 bits incluida en la declaración.|Sí|  
|[\_\_cdecl](../cpp/cdecl.md)|El nombre que sigue usa las convenciones de nomenclatura y llamada de C.|Sí|  
|[\_\_declspec](../cpp/declspec.md)|El nombre que sigue especifica un atributo de clase de almacenamiento específico de Microsoft.|No|  
|[\_\_fastcall](../cpp/fastcall.md)|El nombre que sigue declara una función que usa registros, cuando están disponibles, en lugar de la pila para pasar el argumento.|Sí|  
|[\_\_restrict](../cpp/extension-restrict.md)|Similar a \_\_declspec\([restrict](../cpp/restrict.md)\), pero para usarlo en variables.|No|  
|[\_\_stdcall](../cpp/stdcall.md)|El nombre que sigue especifica una función conforme a la convención de llamada estándar.|Sí|  
|[\_\_w64](../cpp/w64.md)|Marca un tipo de datos como mayor en un compilador de 64 bits.|No|  
|[\_\_unaligned](../cpp/unaligned.md)|Especifica que un puntero a un tipo u otros datos no esté alineado.|No|  
|[\_\_vectorcall](../cpp/vectorcall.md)|El nombre que sigue declara una función que usa registros, incluidos registros de SSE, si están disponibles, en lugar de la pila para el paso de argumentos.|Sí|  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)