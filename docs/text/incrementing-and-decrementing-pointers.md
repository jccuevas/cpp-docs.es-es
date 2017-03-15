---
title: "Aumentar y disminuir punteros | Microsoft Docs"
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
  - "disminuir punteros"
  - "incrementar punteros"
  - "MBCS [C++], punteros"
  - "punteros [C++], caracteres multibyte"
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Aumentar y disminuir punteros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las sugerencias siguientes:  
  
-   Apunte a los bytes iniciales, no a los bytes finales.  Normalmente, es poco seguro utilizar un puntero a un byte final.  Es más seguro examinar una cadena hacia delante y no hacia atrás.  
  
-   Hay macros y funciones de aumento o disminución de punteros que se desplazan un carácter completo:  
  
    ```  
    sz1++;  
    ```  
  
     se convierte en:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     Las funciones `_mbsinc` y `_mbsdec` aumentan y disminuyen correctamente en unidades `character`, con independencia del tamaño del carácter.  
  
-   Para las disminuciones, se necesita un puntero al encabezado de la cadena, como en el siguiente caso:  
  
    ```  
    sz2--;  
    ```  
  
     se convierte en:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     De forma alternativa, el puntero de encabezado podría apuntar a un carácter válido de la cadena, como  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Se debe tener un puntero a un byte inicial válido conocido.  
  
-   Puede que desee mantener un puntero al carácter anterior para obtener llamadas más rápidas a `_mbsdec`.  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)   
 [Índices de byte](../text/byte-indices.md)