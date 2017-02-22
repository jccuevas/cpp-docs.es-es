---
title: "_ITERATOR_DEBUG_LEVEL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ITERATOR_DEBUG_LEVEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ITERATOR_DEBUG_LEVEL"
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _ITERATOR_DEBUG_LEVEL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La macro de `_ITERATOR_DEBUG_LEVEL` \(IDL\) reemplaza y combina la funcionalidad de las macros de [\_SECURE\_SCL](../standard-library/secure-scl.md) \(SCL\) y de [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) \(OCULTADO\).  
  
## Valores macros  
 Las tablas siguientes se resumen los valores para las macros de `_SECURE_SCL` y de `_HAS_ITERATOR_DEBUGGING` y, finalmente cómo esos valores son reemplazados por la macro de `_ITERATOR_DEBUG_LEVEL` .  
  
 La sección siguiente se describen los posibles valores de SCL y las macros HID.  
  
 SCL\=0  
 Deshabilita iteradores comprobados.  
  
 SCL\=1  
 Los permisos protegidos iteradores.  
  
 HID\=0  
 Deshabilita la depuración de iterador en versiones de depuración.  
  
 HID\=1  
 Habilita la depuración de iterador en versiones de depuración.  HID no se puede habilitar en las versiones de lanzamiento.  
  
 La siguiente tabla describe cómo los valores macros IDL reemplazan SCL y de la macro HID.  
  
|Modo de compilación|Nueva macro|Las macros|Descripción|  
|-------------------------|-----------------|----------------|-----------------|  
|**Depurar**||||  
||IDL\=0|SCL\=0, HID\=0|Deshabilita iteradores comprobados y deshabilita la depuración del iterador.|  
||IDL\=1|SCL\=1, HID\=0|Los permisos protegidos iteradores y deshabilita la depuración del iterador.|  
||IDL\=2 \(valor predeterminado\)|SCL\= \(no se aplica\), HID\=1|De forma predeterminada, depuración de iterador de permisos; los iteradores comprobados no son pertinentes.|  
|**Release**||||  
||IDL\=0 \(valor predeterminado\)|SCL\=0|De forma predeterminada, deshabilita iteradores comprobados.|  
||IDL\=1|SCL\=1|Los permisos protegidos iteradores; depuración de iterador no es pertinente.|  
  
## Comentarios  
 En modo de lanzamiento, se produce un error si se especifica IDL\=2.  
  
 Porque macros de `_SECURE_SCL` y de `_HAS_ITERATOR_DEBUGGING` admiten funcionalidad similar, los usuarios suelen ser conocen a ciencia cierta que valor macro y macro a utilizar en una situación concreta.  Para resolver este problema, recomendamos utilizar sólo la macro de `_ITERATOR_DEBUG_LEVEL` .  
  
## Vea también  
 [Bibliotecas seguras: Biblioteca estándar de C\+\+](../standard-library/safe-libraries-cpp-standard-library.md)