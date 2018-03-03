---
title: "Delimitadores para etiquetas de documentación de Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 134605f86ef8019d34f5246fd75abbbf94d40fbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Delimitadores para etiquetas de documentación en Visual C++
El uso de etiquetas de documentación requiere delimitadores, que indican al compilador que un comentario de documentación empieza y termina.  
  
 Puede usar los siguientes tipos de delimitadores con las etiquetas de documentación XML:  
  
 `///`  
 Esta es la forma que se muestran en los ejemplos de documentación y utilizada por las plantillas de proyecto de Visual C++.  
  
 `/** */`  
 Se trata de delimitadores de múltiples líneas.  
  
 Hay algunas reglas de formato cuando se usa el `/** */` delimitadores:  
  
-   Para la línea que contiene el `/**` delimitador, si el resto de la línea es el espacio en blanco, la línea no se procesa para comentarios. Si el primer carácter es un espacio en blanco, se omite ese carácter de espacio en blanco y se procesa el resto de la línea. En caso contrario, todo el texto de la línea situado después del delimitador `/**` se procesa como parte del comentario.  
  
-   Para la línea que contiene el `*/` delimitador, si hay solo espacios en blanco hasta el `*/` delimitador, esa línea se omite. En caso contrario, el texto de la línea hasta el delimitador `*/` se procesa como parte del comentario y está sujeto a las reglas de coincidencia de patrones que se describen en el punto siguiente.  
  
-   Para las líneas después de la que comienza con la `/**` delimitador, el compilador busca un patrón común al principio de cada línea que consta de espacio en blanco opcional y un asterisco (`*`), seguido de más espacio en blanco opcional. Si el compilador encuentra un conjunto común de caracteres al principio de cada línea, omitirá este patrón para todas las líneas después de la `/**` delimitador, hasta y, posiblemente, incluyendo la línea que contiene el `*/` delimitador.  
  
 Algunos ejemplos:  
  
-   La única parte del comentario siguiente que se procesará es la línea que comienza con `<summary>`. Los siguientes formatos de dos etiqueta generará los mismos comentarios:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   El compilador aplica un patrón de "*" para pasar por alto al principio de la segunda y tercera líneas.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario porque no hay ningún asterisco en la segunda línea. Por lo tanto, todo el texto en la segunda y tercera líneas, seguridad hasta el `*/`, se procesará como parte del comentario.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario por dos motivos. En primer lugar, no hay ninguna línea que comienza con un número coherente de espacios antes del asterisco. En segundo lugar, la quinta línea comienza con una tabulación, por lo tanto los espacios no coinciden. Por lo tanto, todo el texto de la segunda línea hasta el `*/` se procesará como parte del comentario.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)