---
title: "Delimitadores para etiquetas de documentaci&#243;n en Visual C++ | Microsoft Docs"
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
  - "documentación XML, delimitadores"
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Delimitadores para etiquetas de documentaci&#243;n en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso de las etiquetas de la documentación requiere los delimitadores, que indican al compilador donde un comentario de documentación empieza y termina.  
  
 Puede utilizar los siguientes tipos de delimitadores con las etiquetas de documentación XML:  
  
 `///`  
 Éste es el formato que se muestra en los ejemplos de la documentación y es utilizado por las plantillas de proyecto de Visual C\+\+.  
  
 `/** */`  
 Éstos son delimitadores de varias líneas.  
  
 Hay algunas reglas de formato al utilizar delimitadores de `/** */` \*\/:  
  
-   Para la línea que contiene el delimitador de `/**`, si el resto de la línea es un espacio en blanco, la línea no se procesan para los comentarios.  Si el primer carácter es un espacio en blanco, se omite ese carácter de espacio en blanco y el resto de la línea se procesa.  En caso contrario, todo el texto de la línea que se encuentra después del delimitador `/**` se procesa como parte del comentario.  
  
-   Para la línea que contiene el delimitador de `*/`, si sólo hay espacio en blanco hasta el delimitador de `*/` , que la línea se omiten.  En caso contrario, el texto que hay en la línea hasta el delimitador `*/` se procesa como parte del comentario, sujeto a las reglas del patrón de coincidencia que se describen en el apartado siguiente:  
  
-   Para línea después del que comienza con el delimitador de `/**` , el compilador busque un modelo común al principio de cada línea que consta del espacio en blanco opcional y un asterisco \(`*`\), seguida por un espacio en blanco más opcional.  Si el compilador encuentra un conjunto común de caracteres al principio de cada línea, omitirá a ese patrón para todas las líneas después del delimitador de `/**` , hasta y posiblemente incluyendo la línea que contiene el delimitador de `*/` .  
  
 Algunos ejemplos:  
  
-   La única parte del siguiente comentario que se procesará es la línea que comienza con `<summary>`.  Los dos siguientes formatos de etiquetas mostrarán los mismos comentarios:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   El compilador se aplica un modelo de “\*” omitir al principio de la segunda y tercera líneas.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario porque no hay asterisco en la segunda línea.  Por consiguiente, todo el texto de la segunda y tercera líneas, arriba hasta de `*/`, se procesará como parte del comentario.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario por dos razones.  Primero, no hay línea que comienza con un número coherente de espacios antes del asterisco.  En segundo lugar, la quinta línea comienza con una etiqueta, que no coincide con los espacios.  Por consiguiente, todo el texto de la segunda línea hasta `*/` se procesarán como parte del comentario.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)