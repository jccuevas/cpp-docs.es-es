---
title: "Caracteres especiales en un archivo MAKE | Microsoft Docs"
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
  - "macros, caracteres especiales"
  - "Make (archivos), caracteres especiales"
  - "NMAKE (programa), caracteres especiales"
  - "caracteres especiales, en macros NMAKE"
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Caracteres especiales en un archivo MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para usar un carácter especial de NMAKE como carácter literal, se ha de colocar delante del mismo un símbolo de intercalación \(^\).  NMAKE omite los símbolos de intercalación que preceden a otros caracteres.  Los caracteres especiales son:  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 Un símbolo de intercalación \(^\) situado dentro de una cadena entre comillas se interpreta como un carácter de intercalación literal.  Un símbolo de intercalación al final de una línea inserta un carácter de nueva línea literal en una cadena o en una macro.  
  
 En macros, una barra inversa \(\\\) seguida de un carácter de nueva línea se sustituye por un espacio.  
  
 En comandos, un signo de porcentaje \(%\) es un especificador de archivos.  Para representar % literalmente en un comando, se ha de especificar un signo de porcentaje doble \(%%\) en lugar de un signo de porcentaje único.  En otras situaciones, NMAKE interpreta un signo de porcentaje único \(%\) literalmente, pero siempre interpreta un signo doble \(%%\) como un signo único \(%\).  Por tanto, para representar un signo %% literal, se han de especificar tres signos de porcentaje %%%, o bien cuatro signos %%%%.  
  
 Para usar el signo de moneda \($\) como un carácter literal en un comando, se han de especificar dos signos de moneda \($$\).  Este método también se puede usar en otras situaciones donde funciona ^$.  
  
## Vea también  
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)