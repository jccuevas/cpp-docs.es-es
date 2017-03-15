---
title: "Especificadores de tipo de datos y equivalentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de datos [C++], equivalentes"
  - "tipos de datos [C++], especificadores"
  - "identificadores, tipo de datos"
  - "tipos enteros con extensión de signo"
  - "tipos simples, nombres"
  - "nombres de tipos [C++], simples"
  - "especificadores de tipos [C++], list"
  - "ampliación de enteros"
  - "extensión de cero"
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Especificadores de tipo de datos y equivalentes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este documento se utilizan normalmente las formas de especificadores de tipos que se incluyen en la tabla siguiente, en lugar de formas largas, y se supone que el tipo `char` es un tipo con signo de forma predeterminada.  Por consiguiente, en este documento, `char` es equivalente a **signed char**.  
  
### Especificadores de tipo y sus equivalentes  
  
|Especificador de tipo|Equivalentes|  
|---------------------------|------------------|  
|**signed char**1|`char`|  
|**signed int**|**signed**, `int`|  
|**signed short int**|**short**, `signed short`|  
|**signed long int**|**long**, **signed long**|  
|`unsigned char`|—|  
|`unsigned int`|`unsigned`|  
|**unsigned short int**|**unsigned short**|  
|**unsigned long int**|`unsigned long`|  
|**float**|—|  
|`long double`2|—|  
  
 1 Cuando hace que `char` sea un tipo sin signo de manera predeterminada \(mediante la opción del compilador \/J\), no puede abreviar **signed char** como `char`.  
  
 2 En los sistemas operativos de 32 bits, el compilador de Microsoft C asigna **long double** al tipo **double**.  
  
 **Específicos de Microsoft**  
  
 Puede especificar la opción del compilador \/J para cambiar el tipo predeterminado de `char` de signed a unsigned.  Cuando esta opción está en efecto, `char` tiene el mismo significado que `unsigned char`, y será preciso utilizar la palabra clave **signed** para declarar un valor de carácter con signo.  Si un valor `char` se declara explícitamente como con signo, la opción \/J no le afecta; el valor se completa con un signo cuando se amplía a un tipo `int`.  El tipo `char` se completa con ceros cuando se amplía al tipo `int`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Especificadores de tipos de C](../c-language/c-type-specifiers.md)