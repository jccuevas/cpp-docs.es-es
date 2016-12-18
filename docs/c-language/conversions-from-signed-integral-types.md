---
title: "Conversiones de tipos enteros con signo | Microsoft Docs"
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
  - "conversiones [C++], integrales"
  - "conversión de tipos de datos [C++], enteros con y sin signo"
  - "enteros, convertir"
  - "conversiones de enteros, con signo"
  - "conversión de tipos [C++], enteros con y sin signo"
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones de tipos enteros con signo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un entero con signo se convierte en un entero sin signo de igual o mayor tamaño y el valor del entero con signo no es negativo, el valor no cambia.  La conversión se realiza extendiendo el signo al entero con signo.  Un entero con signo se convierte en un entero con signo menor truncando los bits de orden superior.  El resultado se interpreta como un valor sin signo, como se muestra en este ejemplo.  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 Cuando un entero con signo se convierte en un valor flotante no se pierde información, aunque sí puede perderse precisión cuando un valor **long int** o **long int sin signo** se convierte en un valor **float**.  
  
 En la tabla siguiente se resumen las conversiones de tipos enteros con signo.  En esta tabla se presupone que el tipo `char` tiene signo de forma predeterminada.  Si usa una opción de tiempo de compilación para cambiar el valor predeterminado del tipo `char` a un tipo sin signo, se aplican las conversiones especificadas en la tabla [Conversiones de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md) para el tipo `unsigned char` en lugar de las conversiones de la tabla siguiente, Conversiones de tipos enteros con signo.  
  
### Conversiones de tipos enteros con signo  
  
|De|Para|Método|  
|--------|----------|------------|  
|`char`1|**short**|Extensión de signo|  
|`char`|**long**|Extensión de signo|  
|`char`|`unsigned char`|Se mantiene el patrón; el bit de orden superior pierde la función de bit con signo|  
|`char`|**unsigned short**|Extensión de signo a **short**; conversión de **short** en **short sin signo**|  
|`char`|`unsigned long`|Extensión de signo a **long**; conversión de **long** a `unsigned long`|  
|`char`|**float**|Extensión de signo a **long**; conversión de **long** a **float**|  
|`char`|**double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|`char`|`long double`|Extensión de signo a **long**; conversión de **long** a **double**|  
|**short**|`char`|Se mantiene el byte de orden inferior|  
|**short**|**long**|Extensión de signo|  
|**short**|`unsigned char`|Se mantiene el byte de orden inferior|  
|**short**|**unsigned short**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|  
|**short**|`unsigned long`|Extensión de signo a **long**; conversión de **long** a `unsigned long`|  
|**short**|**float**|Extensión de signo a **long**; conversión de **long** a **float**|  
|**short**|**double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|**short**|`long double`|Extensión de signo a **long**; conversión de **long** a **double**|  
|**long**|`char`|Se mantiene el byte de orden inferior|  
|**long**|**short**|Se mantiene la palabra de orden inferior|  
|**long**|`unsigned char`|Se mantiene el byte de orden inferior|  
|**long**|**unsigned short**|Se mantiene la palabra de orden inferior|  
|**long**|`unsigned long`|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|  
|**long**|**float**|Se representa como **float**.  Si **long** no se puede representar exactamente, se pierde precisión.|  
|**long**|**double**|Se representa como **double**.  Si **long** no se puede representar exactamente como **double**, se pierde precisión.|  
|**long**|`long double`|Se representa como **double**.  Si **long** no se puede representar exactamente como **double**, se pierde precisión.|  
  
 1.  Todas las entradas de `char` presuponen que el tipo `char` tiene signo de forma predeterminada.  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de 32 bits de Microsoft, un entero es equivalente a un **long**.  La conversión de un valor `int` se realiza de la misma forma que para un valor **long**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)