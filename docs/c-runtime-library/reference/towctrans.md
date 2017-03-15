---
title: "towctrans | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "towctrans"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "towctrans"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "towctrans (función)"
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# towctrans
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transforma un carácter.  
  
## Sintaxis  
  
```  
wint_t towctrans(  
   wint_t c,  
   wctrans_t category   
);  
```  
  
#### Parámetros  
 `c`  
 El carácter que desea transformar.  
  
 `category`  
 Un identificador que contiene el valor devuelto de [wctrans](../../c-runtime-library/reference/wctrans.md).  
  
## Valor devuelto  
 El carácter `c`, después de `towctrans` utilizó la regla de transformación en `category`.  
  
## Comentarios  
 El valor de `category` debe haberse devuelto por una llamada correcta anterior a [wctrans](../../c-runtime-library/reference/wctrans.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`towctrans`|\<wctype.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea `wctrans` para obtener un ejemplo que utiliza `towctrans`.  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)