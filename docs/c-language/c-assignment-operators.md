---
title: "Operadores de asignaci&#243;n de C | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "%= (operador)"
  - "&= (operador)"
  - "*= (operador)"
  - "/= (operador)"
  - "^= (operador), operadores de asignación"
  - "|= (operador)"
  - "+= (operador)"
  - "<<= (operador)"
  - "= (operador)"
  - "-= (operador)"
  - "= (operador), operadores de asignación"
  - ">> (operador)"
  - ">>= (operador)"
  - "conversiones de asignación"
  - "operadores de asignación"
  - "operadores de asignación, C"
  - "operador de asignación y AND bit a bit"
  - "operador de asignación y división"
  - "operador de asignación y multiplicación (*=)"
  - "operador >>=, operadores de asignación de C"
  - "operadores [C], asignación"
  - "operadores [C], desplazamiento"
  - "operador de asignación y resto (%=)"
  - "operadores de desplazamiento a la derecha"
  - "operadores de desplazamiento, derecha"
  - "operador de resta"
  - "operador de resta, operadores de asignación de C"
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de asignaci&#243;n de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una operación de asignación asigna el valor del operando derecho a la ubicación de almacenamiento designada por el operando izquierdo.  Por consiguiente, el operando izquierdo de una operación de asignación debe ser un valor L modificable.  Después de la asignación, una expresión de asignación tiene el valor del operando izquierdo, pero no es un valor L.  
  
 **Sintaxis**  
  
 *assignment\-expression*:  
 *conditional\-expression*  
  
 *unary\-expression assignment\-operator assignment\-expression*  
  
 *assignment\-operator*: uno de  
 **\= \*\=** `/=` `%=` `+=` **–\= \<\<\= \>\>\= &\=** `^=` `|=`  
  
 Los operadores de asignación de C pueden transformar y asignar valores en una única operación.  C proporciona los operadores de asignación siguientes:  
  
|Operador|Operación realizada|  
|--------------|-------------------------|  
|**\=**|Asignación simple|  
|**\*\=**|Asignación y multiplicación|  
|`/=`|Asignación y división|  
|`%=`|Asignación y resto|  
|`+=`|Asignación y suma|  
|**–\=**|Asignación y resta|  
|**\<\<\=**|Asignación y desplazamiento a la izquierda|  
|**\>\>\=**|Asignación y desplazamiento a la derecha|  
|**&\=**|Asignación AND bit a bit|  
|`^=`|Asignación OR exclusivo bit a bit|  
|`&#124;=`|Asignación OR inclusivo bit a bit|  
  
 En la asignación, el tipo del valor derecho se convierte al tipo del valor izquierdo, y el valor se almacena en el operando izquierdo después de que haya ocurrido la asignación.  El operando izquierdo no debe ser una matriz, función o constante.  La ruta de acceso específica de la conversión, que depende de los dos tipos, se describe con detalle en [Conversiones de tipos](../c-language/type-conversions-c.md).  
  
## Vea también  
 [Operadores de asignación](../cpp/assignment-operators.md)