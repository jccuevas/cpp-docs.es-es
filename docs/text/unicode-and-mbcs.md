---
title: "Unicode y MBCS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MBCS [C++], Unicode"
  - "MFC [C++], juegos de caracteres"
  - "juegos de caracteres [C++], multibyte"
  - "bibliotecas en tiempo de ejecución [C++], portabilidad del lenguaje"
  - "juegos de caracteres [C++], Unicode"
  - "Unicode [C++], funciones en tiempo de ejecución de MFC y C"
  - "caracteres multibyte [C++]"
  - "tiempo de ejecución [C++], portabilidad del lenguaje"
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Unicode y MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca MFC \(Microsoft Foundation Classes\), la biblioteca en tiempo de ejecución de C para Visual C\+\+ y el entorno de desarrollo de Visual C\+\+ están habilitados para ayudar al usuario en la programación internacional.  Proporcionan lo siguiente:  
  
-   Compatibilidad con el estándar Unicode en Windows 2000 \(anteriormente Windows NT\).  Unicode es el estándar actual y debe utilizarse siempre que sea posible.  
  
     Unicode es una codificación de caracteres de 16 bits que proporciona suficientes codificaciones para todos los idiomas.  Todos los caracteres ASCII están incluidos en Unicode como caracteres ampliados.  
  
    > [!NOTE]
    >  Windows 95, Windows 98 o Windows Millennium Edition no admiten el estándar Unicode.  
  
-   Compatibilidad con un tipo de juego de caracteres multibyte \(MBCS\) denominado juego de caracteres de doble byte \(DBCS\) en todas las plataformas.  
  
     Los caracteres DBCS están formados por uno o dos bytes.  Algunos intervalos de bytes se reservan para su uso como bytes iniciales.  Un byte inicial especifica que él mismo y el byte final siguiente conforman un solo carácter de dos bytes de ancho.  Se debe mantener un seguimiento de los bytes que son bytes iniciales.  En un juego de caracteres multibyte específico, los bytes iniciales quedan dentro de un intervalo determinado, al igual que los bytes finales.  Si estos intervalos se superponen, puede que sea necesario evaluar el contexto para determinar si un byte específico funciona como byte inicial o como byte final.  
  
-   Compatibilidad con herramientas que simplifican la programación con MBCS de aplicaciones creadas para los mercados internacionales.  
  
     Cuando se ejecuta en una versión habilitada para MBCS del sistema operativo Windows, el sistema de desarrollo Visual C\+\+ \(incluidos el editor de código fuente integrado, el depurador y las herramientas de línea de comandos\) está totalmente habilitado para MBCS.  Para obtener más información, vea [Compatibilidad con MBCS en Visual C\+\+](../text/mbcs-support-in-visual-cpp.md).  
  
> [!NOTE]
>  En esta documentación, MBCS se utiliza para describir toda la compatibilidad no Unicode con caracteres multibyte.  En Visual C\+\+, MBCS siempre significa DBCS.  No se admiten juegos de caracteres con un ancho superior a dos bytes.  
  
 Por definición, el juego de caracteres ASCII es un subconjunto de todos los juegos de caracteres multibyte.  En muchos juegos de caracteres multibyte, cada uno de los caracteres que está en el intervalo de 0x00 a 0x7F es idéntico al carácter que tiene el mismo valor en el juego de caracteres ASCII.  Por ejemplo, tanto en las cadenas de caracteres ASCII como en las MBCS, el carácter **NULL** de un byte \('\\0'\) tiene el valor 0x00 e indica el carácter final nulo.  
  
## Vea también  
 [Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)   
 [Internacionalización](../text/international-enabling.md)