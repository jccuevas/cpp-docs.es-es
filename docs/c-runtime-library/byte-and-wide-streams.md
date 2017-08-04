---
title: Secuencias anchas y de bytes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c916caf1ee0b39567813921401ee02cbda83d222
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="byte-and-wide-streams"></a>Secuencias anchas y de bytes
Una secuencia de bytes trata un archivo como una secuencia de bytes. Dentro del programa, la secuencia es la secuencia de bytes idéntica.  
  
 Por el contrario, una secuencia ancha trata un archivo como una secuencia de caracteres multibyte generalizados, lo que puede tener una amplia gama de reglas de codificación. (Los archivos de texto y binarios todavía se leen y escriben como se describió anteriormente). En el programa, el flujo es similar a la secuencia correspondiente de caracteres anchos. Las conversiones entre las dos representaciones se producen dentro de la biblioteca de C estándar. Las reglas de conversión, en principio, se pueden modificar mediante una llamada a [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) que modifica la categoría `LC_CTYPE`. Cada secuencia ancha determina sus reglas de conversión en el momento en que se convierte en ancha y conserva estas reglas incluso si la categoría `LC_CTYPE` cambia posteriormente.  
  
 El posicionamiento dentro de una secuencia ancha tiene las mismas limitaciones que las secuencias de texto. Además, el indicador de posición de archivo también puede tener que tratar con una codificación dependiente del estado. Normalmente, contiene tanto un desplazamiento de bytes en la secuencia como un objeto de tipo `mbstate_t`. Por lo tanto, la única manera confiable de obtener una posición de archivo dentro de una secuencia ancha consiste en llamar a [fgetpos](../c-runtime-library/reference/fgetpos.md), y la única manera confiable de restaurar una posición obtenida de esta manera consiste en llamar a [fsetpos](../c-runtime-library/reference/fsetpos.md).  
  
## <a name="see-also"></a>Vea también  
 [Archivos y secuencias](../c-runtime-library/files-and-streams.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
