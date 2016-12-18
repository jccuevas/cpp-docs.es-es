---
title: "__pctype_func | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__pctype_func"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__pctype_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__pctype_func"
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __pctype_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera un puntero a una matriz de información de clasificación de carácter.  
  
## Sintaxis  
  
```cpp  
const unsigned short *__pctype_func(  
   )  
```  
  
## Valor devuelto  
 Puntero a una matriz de información de clasificación de carácter.  
  
## Comentarios  
 La información de la tabla de carácter es para uso interno, y usan las distintas funciones que ordenan los caracteres de `char`escrito.  Para obtener más información, vea la sección `Remarks` de [\_pctype, \_pwctype, \_wctype, \_mbctype, \_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_pctype\_func|ctype.h|  
  
## Vea también  
 [\_pctype, \_pwctype, \_wctype, \_mbctype, \_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)