---
title: "Operadores de multiplicaci&#243;n de C | Microsoft Docs"
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
  - "% (operador)"
  - "/ (operador)"
  - "/ (operador), operadores de multiplicación"
  - "operadores aritméticos [C++], operadores de multiplicación"
  - "operador de multiplicación [C++], operadores de multiplicación"
  - "operadores [C], multiplicación"
  - "resto (operador) (%)"
  - "barra diagonal (/): operador"
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operadores de multiplicaci&#243;n de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores multiplicativos realizan operaciones de multiplicación \(**\***\), división \(**\/**\) y resto \(`%`\).  
  
 **Sintaxis**  
  
 *expresión\-multiplicativa*:  
 *expresión\-conversión*  
  
 *expresión\-multiplicativa*  **\***  *expresión\-conversión*  
  
 *expresión\-multiplicativa*  **\/**  *expresión\-conversión*  
  
 *expresión\-multiplicativa*  **%**  *expresión\-conversión*  
  
 Los operandos del operador de resto \(`%`\) deben ser enteros.  Los operadores de multiplicación \(**\***\) y división \(**\/**\) pueden tomar operandos de tipo entero o flotante; los tipos de los operandos pueden ser diferentes.  
  
 Los operadores multiplicativos realizan las conversiones aritméticas usuales en los operandos.  El tipo del resultado es el tipo de los operandos después de la conversión.  
  
> [!NOTE]
>  Como las conversiones realizadas por los operadores multiplicativos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación multiplicativa no se puede representar en el tipo de los operandos después de la conversión.  
  
 A continuación se describen los operadores multiplicativos de C:  
  
|Operador|Descripción|  
|--------------|-----------------|  
|**\***|El operador de multiplicación hace que se multipliquen sus dos operandos.|  
|**\/**|El operador de división hace que el primer operando se divida por el segundo.  Si se dividen dos operandos enteros y el resultado no es un entero, se trunca según las reglas siguientes:|  
||-   El resultado de la división por 0 es indefinido según el estándar ANSI C.  El compilador de C de Microsoft genera un error en tiempo de compilación o en tiempo de ejecución.|  
||-   Si ambos operandos son positivos o sin signo, el resultado se trunca hacia 0.|  
||-   Si alguno de los operandos es negativo, la implementación define si el resultado de la operación es el entero más grande menor o igual que el cociente algebraico o es el entero más pequeño mayor o igual que el cociente algebraico. \(Vea la sección específica de Microsoft más adelante\).|  
|`%`|El resultado del operador de resto es el resto cuando el primer operando se divide por el segundo.  Cuando la división es inexacta, el resultado viene determinado por las reglas siguientes:|  
||-   Si el operando derecho es cero, el resultado es indefinido.|  
||-   Si ambos operandos son positivos o sin signo, el resultado es positivo.|  
||-   Si algún operando es negativo y el resultado es inexacto, el resultado lo define la implementación. \(Vea la sección específica de Microsoft más adelante\).|  
  
 **Específicos de Microsoft**  
  
 En la división donde alguno de los operandos es negativo, la dirección del truncamiento es hacia 0.  
  
 Si alguna operación es negativa en la división con el operador de resto, el resultado tiene el mismo signo que el dividendo \(el primer operando de la expresión\).  
  
 **FIN de Específicos de Microsoft**  
  
## Ejemplos  
 Las declaraciones que se muestran a continuación se utilizan en los ejemplos siguientes:  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 Esta instrucción utiliza el operador de multiplicación:  
  
```  
y = x * i;  
```  
  
 En este caso, `x` se multiplica por `i` para asignar el valor 20,0.  El resultado tiene el tipo **double**.  
  
```  
n = i / j;  
```  
  
 En este ejemplo, 10 se divide por 3.  El resultado se trunca hacia 0, produciendo el valor entero 3.  
  
```  
n = i % j;  
```  
  
 Esta instrucción asigna `n` al resto entero, 1, cuando 10 se divide por 3.  
  
 **Específicos de Microsoft**  
  
 El signo del resto es igual que el signo del dividendo.  Por ejemplo:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 En cada caso, `50` y `2` tienen el mismo signo.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Operadores de multiplicación y el operador de módulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)