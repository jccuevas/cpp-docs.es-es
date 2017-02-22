---
title: "Internacionalizaci&#243;n | Microsoft Docs"
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
  - "globalización [C++], juegos de caracteres"
  - "localización [C++], juegos de caracteres"
  - "MBCS [C++], habilitar"
  - "cadenas [C++], habilitar la internacionalización"
  - "Unicode [C++], habilitar"
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Internacionalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayor parte de los códigos de C y C\+\+ tradicionales realizan suposiciones acerca de la manipulación de cadenas y caracteres que no funcionan correctamente en las aplicaciones internacionales.  Aunque tanto MFC como la biblioteca en tiempo de ejecución admiten Unicode o MBCS, todavía queda trabajo para el programador.  Para guiarle, en esta sección se explica el significado de "internacionalización" en Visual C\+\+:  
  
-   Tanto Unicode como MBCS están habilitados mediante tipos de datos portables en los tipos de valor devueltos y las listas de parámetros de función de MFC.  Estos tipos se definen condicionalmente de forma apropiada, dependiendo de que la versión compilada defina el símbolo **\_UNICODE** o el símbolo **\_MBCS** \(que significa DBCS\).  Distintas variantes de las bibliotecas MFC se vinculan automáticamente a la aplicación, dependiendo de cuál de estos dos símbolos defina la versión compilada.  
  
-   El código de la biblioteca de clases utiliza funciones portables en tiempo de ejecución y otros medios para garantizar el correcto comportamiento de Unicode o MBCS.  
  
-   No obstante, el usuario tiene que controlar ciertos tipos de tareas de internacionalización en el código:  
  
    -   Utilizar las mismas funciones portables en tiempo de ejecución que hagan que MFC sea portable en cada entorno.  
  
    -   Hacer que las cadenas de literales y los caracteres sean portables en cada entorno, mediante la macro **\_T**.  Para obtener más información, vea [Asignaciones de texto genérico en Tchar.h](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md).  
  
    -   Adoptar precauciones al analizar cadenas bajo MBCS.  Estas precauciones no son necesarias bajo Unicode.  Para obtener más información, vea [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md).  
  
    -   Adoptar precauciones si se mezclan caracteres ANSI \(8 bits\) y Unicode \(16 bits\) en la aplicación.  Se pueden utilizar caracteres ANSI en algunas partes del programa y caracteres Unicode en otras, pero no se pueden mezclar en la misma cadena.  
  
    -   No integrar como parte del código las cadenas de la aplicación.  En su lugar, se deben convertir en recursos STRINGTABLE agregándolas al archivo .rc de la aplicación.  Posteriormente, la aplicación se puede localizar sin que sea necesario recompilar ni efectuar cambios en el código fuente.  Para obtener más información acerca de los recursos STRINGTABLE, vea [Editor de cadenas](../mfc/string-editor.md).  
  
> [!NOTE]
>  Los juegos de caracteres europeos y MBCS tienen algunos caracteres, como las letras acentuadas, con códigos de carácter superiores a 0x80.  Como la mayoría del código utiliza caracteres con signo, estos caracteres superiores a 0x80 se extienden mediante signo cuando se convierten en `int`.  Esto supone un problema para la indización de matrices, ya que los caracteres extendidos con signo que sean negativos indizan fuera de la matriz.  Los idiomas que utilizan MBCS, como el japonés, son también únicos.  Dado que un carácter podría constar de 1 o 2 bytes, siempre debería manipular ambos bytes a la vez.  
  
## Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Estrategias de internacionalización](../text/internationalization-strategies.md)