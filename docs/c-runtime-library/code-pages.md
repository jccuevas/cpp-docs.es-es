---
title: "P&#225;ginas de c&#243;digos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.international"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ANSI [C++], páginas de códigos"
  - "juegos de caracteres [C++], páginas de códigos"
  - "páginas de códigos [C++], tipos de"
  - "páginas de códigos de configuración regional [C++]"
  - "localización [C++], páginas de códigos"
  - "páginas de códigos multibyte [C++]"
  - "página de códigos predeterminada del sistema"
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# P&#225;ginas de c&#243;digos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`code page` es un juego de caracteres, que puede incluir números, signos de puntuación, y otros glifos.  Los lenguajes diferentes y configuraciones regionales pueden utilizar páginas de códigos distintas.  Por ejemplo, la página de códigos ANSI 1252 se utiliza para el inglés y la mayoría de idiomas europeos; La página de códigos OEM 932 se utiliza para los caracteres Kanji del japonés.  
  
 Una página de códigos se puede representar en una tabla como una asignación de caracteres a los valores de solo\- byte o valores multibyte.  Muchas páginas de códigos comparten el juego de caracteres ASCII de caracteres en el intervalo de 0x00 a 0x7F.  
  
 La biblioteca en tiempo de ejecución de Microsoft utiliza los siguientes tipos de páginas de códigos:  
  
-   Página de códigos ANSI del Sistema\- predeterminado.  De forma predeterminada, al iniciar el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte a la página de códigos ANSI del sistema\- predeterminado, que se obtiene del sistema operativo.  La llamada:  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     también establece la configuración regional en la página de códigos ANSI del sistema\- predeterminado.  
  
-   Página de códigos de la configuración regional.  El comportamiento de varias rutinas de servicio depende de la configuración regional actual, que incluye la página de códigos de la configuración regional. \(Para obtener más información, vea [Rutinas Configuración regional\-dependientes](../c-runtime-library/locale.md).\) De forma predeterminada, todas las rutinas configuración regional\- dependientes en la biblioteca en tiempo de ejecución de Microsoft utilizan la página de códigos que corresponde a “C” la configuración regional.  En tiempo de ejecución puede cambiar o ver la página de códigos de la configuración regional en uso con una llamada a [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   Página de códigos de Multibyte.  El comportamiento la mayoría de las rutinas de multibyte\- carácter en la biblioteca en tiempo de ejecución depende de paginación actual de código multibyte.  De forma predeterminada, estas rutinas utilizan la página de códigos ANSI del sistema\- predeterminado.  En tiempo de ejecución puede ver y cambiar la página de códigos multibyte con [\_getmbcp](../c-runtime-library/reference/getmbcp.md) y [\_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivamente.  
  
-   La configuración regional “c” es definida por ANSI que corresponda a la configuración regional en la que los programas de c se han ejecutado tradicionalmente.  La página de códigos de la configuración regional “c” \(página de códigos “c”\) corresponde al juego de caracteres ASCII.  Por ejemplo, en la configuración regional “c”, `islower` devuelve true para los valores 0x61 – 0x7A únicamente.  En otra configuración regional, `islower` puede devolver true para estas junto con otros valores, definidos por esa configuración regional.  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)