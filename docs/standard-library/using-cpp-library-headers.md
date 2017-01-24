---
title: "Usar encabezados de la biblioteca de C++ | Microsoft Docs"
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
helpviewer_keywords: 
  - "encabezados"
  - "encabezados, asignación de nombres en la directiva include de C++"
  - "encabezados, Biblioteca estándar de C++"
  - "INCLUDE (directiva)"
  - "encabezados de biblioteca"
  - "Biblioteca estándar de C++, encabezados"
  - "encabezado estándar de C++"
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar encabezados de la biblioteca de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se incluye el contenido de un encabezado estándar llamarlo en una directiva include.  
  
```  
#include <iostream>   // include I/O facilities  
```  
  
 Puede incluir los encabezados estándar en cualquier orden, un encabezado estándar más de una vez, o dos o más encabezados estándar que definen la misma macro o el mismo tipo.  No incluye un encabezado estándar de una declaración.  No defina macros que tienen los mismos nombres que las palabras clave antes de que incluye un encabezado estándar.  
  
 El encabezado de la biblioteca de c\+\+. incluye cualquier otro encabezado de biblioteca de C\+\+ que necesite definir tipos necesarios. \(Siempre incluyen explícitamente que cualquier encabezado de biblioteca de C\+\+ necesarias en una unidad de traducción, sin embargo, al final del conjeture mal sobre sus dependencias reales.\) Un encabezado estándar de C nunca incluye otro encabezado estándar.  Un encabezado estándar declara o define sólo las entidades descritas para él en este documento.  
  
 Cada función de biblioteca se declara en un encabezado estándar.  A diferencia de c estándar, el encabezado estándar nunca proporciona una macro de enmascarado con el mismo nombre que la función que enmascara la declaración de función y alcanza el mismo efecto.  Para obtener más información acerca de las macros de máscara, vea [Convenciones de la biblioteca de C\+\+](../standard-library/cpp-library-conventions.md).  
  
 Todos los nombres distinto de `operator delete` y de `operator new` en los encabezados de la biblioteca de C\+\+ se definen en el espacio de nombres `std` , o en un espacio de nombres anidado dentro del espacio de nombres `std` .  Se hace referencia al nombre `cin`, por ejemplo, como `std::cin`.  La nota, sin embargo, que los nombres de macro no están sujetos a la calificación de espacio de nombres, por lo que escribe siempre `__STD_COMPLEX` sin un calificador de espacio de nombres.  
  
 En algunos entornos de traducción, incluir el encabezado de la biblioteca de c\+\+. puede alzar los nombres externos declarados en el espacio de nombres `std` en el espacio de nombres global también, con declaraciones individuales de `using` para cada uno de los nombres.  Si no, el encabezado no presenta ninguna nombres de biblioteca en el espacio de nombres actual.  
  
 El estándar de C\+\+ requiere que los encabezados estándar de C declaran todos los nombres externos en el espacio de nombres `std`, los mejora en el espacio de nombres global con declaraciones individuales de `using` para cada uno de los nombres.  Pero en algunos entornos de traducción los encabezados estándar de C no incluyen ninguna declaración de espacio de nombres, declarando todos los nombres directamente en el espacio de nombres global.  Así, la manera más portátil de tratar de espacios de nombres es realizar dos reglas:  
  
-   Para confianza declarar en el espacio de nombres `std` un nombre externo que se declara tradicionalmente en \<stdlib.h, por\>ejemplo, incluye el cstdlib de encabezado \<.\>  Sabe que el nombre también se puede declarar en el espacio de nombres global.  
  
-   Para confianza declarar en el espacio de nombres global un nombre externo declarado en \<stdlib.h, incluya\>el encabezado stdlib.h \<directamente\> .  Sabe que el nombre también se puede declarar en el espacio de nombres `std`.  
  
 Así, si desea llamar `std::abort` para producir la terminación anormal, debe incluir \<el cstdlib\>.  Si desea llamar `abort`, debe incluir \<stdlib.h.\>  
  
 O bien, puede escribir la declaración:  
  
```  
using namespace std;  
```  
  
 qué aporta todos los nombres de biblioteca en el espacio de nombres actual.  Si escribe directivas include de esta declaración inmediatamente después de todo, se mejora los nombres en el espacio de nombres global.  Puede omitir posteriormente consideraciones de espacio de nombres en el resto de la unidad de traducción.  También impide la mayoría de las diferencias entre diferentes entornos de traducción.  
  
 A menos que se indica específicamente de otra forma, no puede definir nombres en el espacio de nombres `std` , o en un espacio de nombres anidado dentro del espacio de nombres `std` , dentro del programa.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)