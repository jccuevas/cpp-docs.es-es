---
title: "Configuraciones regionales y p&#225;ginas de c&#243;digos | Microsoft Docs"
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
  - "juegos de caracteres [C++], páginas de códigos"
  - "juegos de caracteres [C++], configuraciones regionales"
  - "páginas de códigos [C++]"
  - "páginas de códigos [C++], cambio dinámico"
  - "páginas de códigos [C++], configuraciones regionales"
  - "convenciones [C++], compatibilidad con caracteres internacionales"
  - "identificadores de configuración regional [C++]"
  - "configuraciones regionales [C++]"
  - "configuraciones regionales [C++], acerca de las configuraciones regionales"
  - "localización [C++], páginas de códigos"
  - "localización [C++], configuraciones regionales"
  - "páginas de códigos multibyte [C++]"
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Configuraciones regionales y p&#225;ginas de c&#243;digos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un identificador de configuración regional refleja el idioma y las convenciones locales de una determinada zona geográfica.  Un idioma determinado se puede hablar en varios países o regiones; por ejemplo, el portugués se habla en Portugal y Brasil.  A la inversa, una región o un país pueden tener más de un idioma oficial.  Por ejemplo, Canadá tiene dos idiomas, el inglés y el francés.  Es decir, Canadá tiene dos configuraciones regionales distintas, el inglés canadiense y el francés canadiense.  Entre las categorías dependientes de la configuración regional se encuentran el formato de fechas y el formato de presentación de valores de moneda.  
  
 El idioma determina las convenciones de formato de datos y texto, mientras que el país o la región determinan las convenciones locales.  Cada idioma tiene una asignación única, representada por páginas de códigos, que incluye caracteres distintos de los del alfabeto \(como los signos de puntuación y los números\).  Una página de códigos es un juego de caracteres y está relacionada con el idioma.  Como tal, una [configuración regional](../c-runtime-library/locale.md) es una combinación única de idioma, país o región y de página de códigos.  La configuración regional y de la página de códigos se puede modificar en tiempo de ejecución si se llama a la función [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Idiomas distintos pueden utilizar páginas de códigos distintas.  Por ejemplo, la página de códigos ANSI 1252 se utiliza para el inglés y para la mayoría de idiomas europeos, mientras que la página de códigos ANSI 932 se utiliza para los caracteres Kanji del japonés.  La práctica totalidad de páginas de códigos comparten el juego de caracteres ASCII para los 128 caracteres inferiores \(de 0x00 a 0x7F\).  
  
 Una página de códigos de un solo byte se puede representar en una tabla \(con 256 entradas\) como una asignación de valores de byte a caracteres \(incluidos números y signos de puntuación\), o glifos.  Una página de códigos multibyte también se puede representar como una tabla de gran tamaño \(con 64.000 entradas\) de valores de doble byte a caracteres.  Sin embargo, en la práctica, normalmente se representan como una tabla para los primeros 256 caracteres \(un solo byte\) y como intervalos para los valores de doble byte.  
  
 Para obtener más información acerca de las páginas de códigos, vea [Páginas de códigos](../c-runtime-library/code-pages.md).  
  
 La biblioteca en tiempo de ejecución de C tiene dos tipos de páginas de códigos internas: regionales y multibyte.  Se puede cambiar la página de códigos actual durante la ejecución de un programa \(vea la documentación para las funciones [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) y [\_setmbcp](../c-runtime-library/reference/setmbcp.md)\).  Además, la biblioteca en tiempo de ejecución puede obtener y utilizar el valor de la página de códigos del sistema operativo.  En Windows 2000, la página de códigos del sistema operativo es la página de códigos "ANSI predeterminada del sistema".  Esta página de códigos es constante a lo largo de la ejecución del programa.  
  
 Cuando la página de códigos regional cambia, el comportamiento del conjunto de funciones dependiente de la configuración regional cambia a lo que indica la página de códigos elegida.  De forma predeterminada, todas las funciones dependientes de la configuración regional empiezan a ejecutarse con una página de códigos regional única de la configuración regional "C".  Se puede cambiar la página de códigos regional interna \(así como otras propiedades específicas de la configuración regional\) llamando a la función `setlocale`.  Una llamada a la función `setlocale`\(LC\_ALL, ""\) establece la configuración regional en lo que indica la configuración regional de usuario del sistema operativo.  
  
 De forma similar, cuando la página de códigos multibyte cambia, el comportamiento de las funciones multibyte cambia a lo que indica la página de códigos elegida.  De forma predeterminada, todas las funciones multibyte empiezan a ejecutarse con una página de códigos multibyte correspondiente a la página de códigos predeterminada del sistema operativo.  Se puede cambiar la página de códigos multibyte interna llamando a la función `_setmbcp`.  
  
 La función en tiempo de ejecución de C `setlocale` establece, cambia o consulta una parte o la totalidad de la información relativa a la configuración regional del programa actual.  La rutina [\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) es una versión de caracteres anchos de `setlocale`; los argumentos y valores devueltos de `_wsetlocale` son cadenas de caracteres anchos.  
  
## Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Ventajas de la portabilidad de los juegos de caracteres](../text/benefits-of-character-set-portability.md)