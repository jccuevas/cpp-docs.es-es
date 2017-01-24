---
title: "Constantes de punto flotante de C | Microsoft Docs"
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
  - "constantes, punto flotante"
  - "double (tipo de datos), constantes de punto flotante"
  - "constantes de punto flotante"
  - "constantes de punto flotante, acerca de las constantes de punto flotante"
  - "números de punto flotante, constantes de punto flotante"
  - "tipos [C], constantes"
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Constantes de punto flotante de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una "constante de punto flotante" es un número decimal que representa un número real con signo.  La representación de un número real con signo incluye una parte entera, una parte fraccionaria y un exponente.  Utilice constantes de punto flotante para representar valores de punto flotante que no se pueden modificar.  
  
## Sintaxis  
 *floating\-point\-constant*:  
 *fractional\-constant exponent\-part*  opt *floating\-suffix* opt  
  
 *digit\-sequence exponent\-part floating\-suffix*  opt  
  
 *fractional\-constant*:  
 *digit\-sequence*  opt **.** *digit\-sequence*  
  
 *digit\-sequence*  **.**  
  
 *exponent\-part*:  
 **e**  *sign*  opt *digit\-sequence*  
  
 **E**  *sign*  opt *digit\-sequence*  
  
 *sign* : one of  
 **\+ –**  
  
 *digit\-sequence*:  
 *digit*  
  
 *digit\-sequence digit*  
  
 *floating\-suffix* : one of  
 **f l F L**  
  
 Se pueden omitir los dígitos que hay delante del separador decimal \(la parte entera del valor\) o los dígitos que hay detrás del separador decimal \(la parte fraccionaria\), pero no ambos.  Solo se puede omitir el separador decimal si se incluye un exponente.  No se pueden utilizar caracteres de espacio en blanco para separar los dígitos o los caracteres de la constante.  
  
 En los ejemplos siguientes se muestran algunas formas de constantes y expresiones de punto flotante:  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 Las constantes de punto flotante son positivas a menos que vayan precedidas de un signo menos \(**–**\).  En este caso, el signo menos se trata como un operador unario de negación aritmética.  Las constantes de punto flotante tienen el tipo **float**, **double** o `long double`.  
  
 Una constante de punto flotante sin un sufijo **f**, **F**, **l** o **L** tiene el tipo **double**.  Si el sufijo es la letra **f** o **F**, la constante tiene el tipo **float**.  Si el sufijo es la letra **l** o **L**, tiene el tipo `long double`.  Por ejemplo:  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 Tenga en cuenta que el compilador de Microsoft C asigna **long double** al tipo **double**.  Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tipos **double**, **float** y **long**.  
  
 Se puede omitir la parte entera de la constante de punto flotante, como se muestra en los ejemplos siguientes.  El número .75 se puede expresar de muchas maneras, incluidas las siguientes:  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## Vea también  
 [Constantes de C](../c-language/c-constants.md)