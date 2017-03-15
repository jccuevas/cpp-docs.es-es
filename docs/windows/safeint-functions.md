---
title: "SafeInt (Funciones) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones, SafeInt"
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 13
---
# SafeInt (Funciones)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca SafeInt proporciona varias funciones que puede utilizar sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  Si desea proteger una sola operación matemática de desbordamiento con enteros, puede utilizar estas funciones.  Si desea proteger varias operaciones matemáticas, debe crear objetos de `SafeInt` .  Es más eficaz crear objetos de `SafeInt` que utilizar estos tiempos de varias funciones.  
  
 Estas funciones permiten comparar o realizar operaciones matemáticas en dos tipos de parámetros sin tener que convertirlos a un mismo tipo primero.  
  
 Cada una de estas funciones tiene dos tipos de plantilla: `T` y `U`.  Cada uno de estos tipos puede ser un booleano, un carácter, o un tipo entero.  Los tipos enteros pueden ser firmados o sin firmar y cualquier tamaño a partir de 8 bits a 64 bits.  
  
## En esta sección  
  
|Función|Descripción|  
|-------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Suma dos números y los protege contra el desbordamiento.|  
|[SafeCast](../windows/safecast.md)|Conversiones de un tipo de parámetro a otro tipo.|  
|[SafeDivide](../windows/safedivide.md)|Divide dos números y los protege contra dividir por cero.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [SafeNotEquals](../Topic/SafeNotEquals.md)|Compara dos números.  Estas funciones permiten comparar dos tipos de números sin cambiar sus tipos.|  
|[SafeModulus](../windows/safemodulus.md)|Realiza la operación de módulo en dos números.|  
|[SafeMultiply](../Topic/SafeMultiply.md)|Multiplica dos números juntos y los protege contra el desbordamiento.|  
|[SafeSubtract](../windows/safesubtract.md)|Resta dos números y los protege contra el desbordamiento.|  
  
## Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[SafeInt \(Clase\)](../windows/safeint-class.md)|Clase `SafeInt`|  
|[SafeIntException \(Clase\)](../windows/safeintexception-class.md)|El específico de la clase de excepción en la biblioteca SafeInt.|