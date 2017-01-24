---
title: "/RAWDATA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rawdata"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RAWDATA (opción de dumpbin)"
  - "datos sin formato"
  - "RAWDATA (opción de dumpbin)"
  - "-RAWDATA (opción de dumpbin)"
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RAWDATA
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## Comentarios  
 Esta opción muestra el contenido sin formato de cada sección del archivo.  Los argumentos controlan el formato de presentación de la forma descrita a continuación:  
  
|Argumento|Resultado|  
|---------------|---------------|  
|1|El valor predeterminado.  El contenido se muestra en bytes hexadecimales y también en caracteres ASCII si tienen una representación impresa.|  
|2|El contenido se muestra como valores hexadecimales de 2 bytes.|  
|4|El contenido se muestra como valores hexadecimales de 4 bytes.|  
|8|El contenido se muestra como valores hexadecimales de 8 bytes.|  
|\(Ninguno\)|Se suprimen los datos sin procesar.  Este argumento es útil para controlar el resultado de la opción \/ALL.|  
|*Número*|El ancho de las líneas mostradas se establece en un valor de `number` valores por línea.|  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)