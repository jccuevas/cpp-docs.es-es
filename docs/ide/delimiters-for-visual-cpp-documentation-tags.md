---
title: Delimitadores para etiquetas de documentación en Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4d22df877ab757134ee6da86a5ff22ec106f958
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208580"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Delimitadores para etiquetas de documentación en Visual C++
El uso de etiquetas de documentación requiere delimitadores, que indican al compilador dónde empieza y dónde acaba un comentario de documentación.  
  
 Puede usar los siguientes tipos de delimitadores con las etiquetas de documentación XML:  
  
 `///`  
 Este es el formato que se muestra en los ejemplos de documentación y que usan las plantillas de proyecto de Visual C++.  
  
 `/** */`  
 Se trata de delimitadores de múltiples líneas.  
  
 Hay varias reglas de formato cuando se usan los delimitadores `/** */`:  
  
-   Para la línea que contiene el delimitador `/**`, si el resto de la línea es espacio en blanco, la línea no se procesa en busca de comentarios. Si el primer carácter es un espacio en blanco, ese carácter de espacio en blanco se omite y se procesa el resto de la línea. En caso contrario, todo el texto de la línea situado después del delimitador `/**` se procesa como parte del comentario.  
  
-   Para la línea que contiene el delimitador `*/`, si solo hay espacio en blanco hasta el delimitador `*/`, esa línea se omite. En caso contrario, el texto de la línea hasta el delimitador `*/` se procesa como parte del comentario y está sujeto a las reglas de coincidencia de patrones que se describen en el punto siguiente.  
  
-   Para las líneas después de la que comienza con el delimitador `/**`, el compilador busca un patrón común al principio de cada línea que consta de espacio en blanco opcional y un asterisco (`*`), seguido de más espacio en blanco opcional. Si el compilador encuentra un conjunto común de caracteres al principio de cada línea, omitirá este patrón para todas las líneas después del delimitador `/**`, hasta y, posiblemente, incluyendo la línea que contiene el delimitador `*/`.  
  
 Algunos ejemplos:  
  
-   La única parte del comentario siguiente que se procesará es la línea que comienza con `<summary>`. Los dos formatos de etiqueta siguientes generarán los mismos comentarios:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   El compilador aplica un patrón de " \* " para ignorar al principio de la segunda y la tercera línea.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario porque no hay ningún asterisco en la segunda línea. Por tanto, todo el texto de la segunda y la tercera línea, hasta `*/`, se procesará como parte del comentario.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   El compilador no encuentra ningún patrón en este comentario por dos razones. En primer lugar, no hay ninguna línea que comience con un número coherente de espacios antes del asterisco. En segundo lugar, la quinta línea comienza con una tabulación, por lo tanto los espacios no coinciden. Por tanto, todo el texto de la segunda línea, hasta `*/`, se procesará como parte del comentario.  
  
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