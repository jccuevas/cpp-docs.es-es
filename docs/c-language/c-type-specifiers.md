---
title: "Especificadores de tipos de C | Microsoft Docs"
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
  - "especificadores, tipo"
  - "especificadores de tipos, C"
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Especificadores de tipos de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los especificadores de tipo en las declaraciones definen el tipo de una declaración de variable o de función.  
  
## Sintaxis  
 *type\-specifier*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 Los tipos **signed char**, **signed int**, **signed short int** y **signed long int**, así como sus homólogos `unsigned` y `enum`, se denominan tipos "enteros".  Los especificadores de tipo **float**, **double** y `long double` se conocen como tipos "flotantes" o de "punto flotante".  Se puede utilizar cualquier especificador de tipo entero o de punto flotante en una declaración de variable o de función.  Si no se proporciona un *type\-specifier* en una declaración, se considera que es `int`.  
  
 Las palabras clave opcionales **signed** y `unsigned` pueden ir precedidas o seguidas de cualquiera de los tipos enteros, excepto `enum`, y también se pueden utilizar solas como especificadores de tipo, en cuyo caso se entienden como **signed int** y `unsigned int`, respectivamente.  Cuando la palabra clave `int` se usa sola, se da por supuesto que es **signed**.  Cuando las palabras clave **long** y **short** se utilizan solas, se entienden como **long int** y `short int`.  
  
 Los tipos de enumeración se consideran tipos básicos.  Los especificadores para los tipos de enumeración se describen en [Declaraciones de enumeración](../c-language/c-enumeration-declarations.md).  
  
 La palabra clave `void` tiene tres usos: especificar un tipo de valor devuelto de función, especificar una lista de tipos de argumento para una función que no toma ningún argumento y especificar un puntero a un tipo sin especificar.  El tipo `void` se puede utilizar para declarar funciones que no devuelven ningún valor o para declarar un puntero a un tipo sin especificar.  Vea [Argumentos](../c-language/arguments.md) para obtener información sobre el tipo `void` cuando aparece solo entre paréntesis después de un nombre de función.  
  
 **Específicos de Microsoft**  
  
 La comprobación de tipos es ahora compatible con ANSI, lo que significa que `int` y **short** son tipos distintos.  Por ejemplo, esto es una nueva definición en el compilador de Microsoft C que se aceptaba en versiones anteriores del compilador.  
  
```  
int   myfunc();  
short myfunc();  
```  
  
 En el ejemplo siguiente también se genera una advertencia sobre el direccionamiento indirecto a tipos diferentes:  
  
```  
int *pi;  
short *ps;  
  
ps = pi;  /* Now generates warning */  
```  
  
 El compilador de Microsoft C también genera advertencias para las diferencias de signo.  Por ejemplo:  
  
```  
signed int *pi;  
unsigned int *pu  
  
pi = pu;  /* Now generates warning */  
```  
  
 Las expresiones de tipo `void` se evalúan para ver si tienen efectos secundarios.  No se puede utilizar el valor \(inexistente\) de una expresión que tiene el tipo `void` de ninguna forma, ni puede convertirse una expresión `void` \(mediante conversión implícita o explícita\) a ningún tipo, excepto `void`.  Si utiliza una expresión de cualquier otro tipo en un contexto donde se requiere una expresión `void`, se descarta el valor.  
  
 Por conformidad con la especificación ANSI, **void\*\*** no se puede utilizar como **int\*\***.  Solo **void\*** se puede utilizar como puntero a un tipo sin especificar.  
  
 **FIN de Específicos de Microsoft**  
  
 Se pueden crear especificadores de tipo adicionales con declaraciones `typedef`, como se describe en [Declaraciones typedef](../c-language/typedef-declarations.md).  Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre el tamaño de cada tipo.  
  
## Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)