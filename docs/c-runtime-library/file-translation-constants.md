---
title: "Constantes de traducci&#243;n de archivo | Microsoft Docs"
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
  - "c.constants.file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "constantes [C++], modo de traducción de archivos"
  - "traducción de archivos [C++]"
  - "traducción de archivos [C++], constantes"
  - "constantes de traducción"
  - "traslación, constantes"
  - "traslación, constantes de traducción de archivo"
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes de traducci&#243;n de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## Comentarios  
 Estas constantes se especifica el modo de traducción \(**"b"** o **"t"**\).  Incluyen el modo en la cadena que especifica el tipo de acceso \(**"r"**, **"w"**, **"a"**, **"r\+"**, **"w\+"**, **"a\+"**\).  
  
 Los modos de traducción son los siguientes:  
  
 **t**  
 Abrir en modo de texto \(traducido\).  En este modo, las combinaciones de retorno de carro\/avance de línea \(CR\-LF\) se convierten en los únicos avances de línea \(LF\) en la entrada, y caracteres de LF se convierten en combinaciones de CR\-LF en la salida.  Además, CTRL\+Z se interpreta como carácter de final de archivo en la entrada.  En archivos abierto para lectura o lectura\/escritura, comprobaciones de `fopen` CTRL\+Z al final del archivo y colóquelo, si es posible.  Se hace esto porque usar las funciones de `fseek` y de `ftell` para desplazarse dentro de un final de archivo con CTRL\+Z puede hacer `fseek` para comportarse incorrectamente cerca del final del archivo.  
  
> [!NOTE]
>  La opción de **v** no forma parte del estándar ANSI para `fopen` y `freopen`.  Es una extensión de Microsoft y no se debe utilizar donde desee la portabilidad de ANSI.  
  
 **t**  
 Abrir en modo \(sin traducir\) binario.  Se suprimen las conversiones anteriores.  
  
 Si **v** o **t** no se da en *modo*, el de modalidad de traducción está definida por la variable [\_fmode](../c-runtime-library/fmode.md)de valor por defecto\- modo.  Para obtener más información sobre cómo utilizar los modos de texto y el binario, vea [E\/S de archivo de texto y el modo binario](../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## Vea también  
 [\_fdopen, \_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, \_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen, \_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)