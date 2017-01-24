---
title: "bitset (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bitset/std::bitset"
  - "std::bitset"
  - "std.bitset"
  - "bitset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitset (clase)"
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bitset (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un tipo de objeto que almacena una secuencia que consta de un número fijo de bits que proporcionan una manera compacta de mantener indicadores para un conjunto de elementos o condiciones.  La clase bitset admite operaciones en objetos de tipo bitset que contienen una colección de bits y proporcionan acceso de tiempo constante a cada bit.  
  
## Sintaxis  
  
```  
  
     template <size_t   
     N  
     >  
class bitset  
```  
  
#### Parámetros  
 *N*  
 Especifica el número de bits del objeto bitset con un entero distinto de cero de tipo **size\_t** que deben conocerse en tiempo de compilación.  
  
## Comentarios  
 A diferencia de la clase similar [vector \<bool\>](../standard-library/vector-bool-class.md), la clase bitset no tiene iteradores y no es un contenedor de la Biblioteca de plantillas estándar.  También se distingue de vector\<bool\> en que es de un determinado tamaño específico que se fija en tiempo de compilación de acuerdo con el tamaño especificado por el parámetro de plantilla **N** cuando se declara **bitset\<N\>**.  
  
 Un bit se establece si su valor es 1 y se restablece si su valor es 0.  Voltear o alternar un bit es cambiar su valor de 1 a 0 o de 0 a 1.  Los bits **N** de un bitset están indizados por valores enteros de 0 a **N**\-1, donde 0 indiza la posición del primer bit y **N**\-1 la posición del último bit.  
  
### Constructores  
  
|||  
|-|-|  
|[bitset](../Topic/bitset::bitset.md)|Construye un objeto de clase `bitset<N>` e inicializa los bits a cero, hasta un valor especificado o hasta los valores obtenidos de los caracteres de una cadena.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[element\_type](../Topic/bitset::element_type.md)|Tipo sinónimo del tipo de datos `bool` y que se puede usar para hacer referencia a los bits de elemento en un `bitset`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[todas](../Topic/bitset::all.md)|Comprueba todos los bits de este `bitset` para determinar si están establecidos en `true`.|  
|[cualquiera](../Topic/bitset::any.md)|Función miembro que comprueba si cualquiera de los bits de la secuencia está establecido en 1.|  
|[count](../Topic/bitset::count.md)|Función miembro que devuelve el número de bits establecidos en la secuencia de bits.|  
|[voltear](../Topic/bitset::flip.md)|Alterna el valor de todos los bits de un `bitset` o de un solo bit en una posición especificada.|  
|[ninguna](../Topic/bitset::none.md)|Comprueba si no se ha establecido ningún bit en 1 en un objeto `bitset`.|  
|[restablecer](../Topic/bitset::reset.md)|Restablece todos los bits en un `bitset` en 0 o restablece un bit en una posición especificada en 0.|  
|[establecer](../Topic/bitset::set.md)|Establece todos los bits en un `bitset` en 1 o establece un bit en una posición especificada en 1.|  
|[size](../Topic/bitset::size.md)|Devuelve el número de bits de un objeto `bitset`.|  
|[prueba](../Topic/bitset::test.md)|Comprueba si el bit de una posición especificada en un `bitset` está establecido en 1.|  
|[to\_string](../Topic/bitset::to_string.md)|Convierte un objeto `bitset` en una representación de cadena.|  
|[to\_ullong](../Topic/bitset::to_ullong.md)|Devuelve la suma de los valores de bits en el `bitset` como un `unsigned long long`.|  
|[to\_ulong](../Topic/bitset::to_ulong.md)|Convierte un objeto `bitset` en el `unsigned long` que generaría la secuencia de bits contenida si se usase para inicializar el `bitset`.|  
  
### Clases de miembro  
  
|||  
|-|-|  
|[referencia](../Topic/bitset::reference.md)|Clase de proxy que proporciona referencias a los bits que contiene un `bitset` y que se usa para acceder y manipular los bits individuales como una clase auxiliar para el `operator[]` de clase `bitset`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/bitset::operator!=.md)|Comprueba si hay desigualdad entre un `bitset` de destino y un `bitset` especificado.|  
|[operator&\=](../Topic/bitset::operator&=.md)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `AND` lógica.|  
|[operador \<\<](../Topic/bitset::operator%3C%3C.md)|Desplaza los bits de un `bitset` a la izquierda un número especificado de posiciones y devuelve el resultado a un nuevo `bitset`.|  
|[operator\<\<\=](../Topic/bitset::operator%3C%3C=.md)|Desplaza los bits de un `bitset` a la izquierda un número especificado de posiciones y devuelve el resultado al `bitset` de destino.|  
|[operator\=\=](../Topic/bitset::operator==.md)|Comprueba si hay igualdad entre un `bitset` de destino y un `bitset` especificado.|  
|[operador \>\>](../Topic/bitset::operator%3E%3E.md)|Desplaza los bits de un `bitset` a la derecha un número especificado de posiciones y devuelve el resultado a un nuevo `bitset`.|  
|[operator\>\>\=](../Topic/bitset::operator%3E%3E=.md)|Desplaza los bits de un `bitset` a la derecha un número especificado de posiciones y devuelve el resultado al `bitset` de destino.|  
|[operator&#91;&#93;](../Topic/bitset::operator.md)|Devuelve una referencia a un bit en una posición especificada en un `bitset` si el `bitset` es modificable; en caso contrario, devuelve el valor del bit en esa posición.|  
|[operator^\=](../Topic/bitset::operator%5E=.md)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` exclusiva.|  
|[operator&#124;\=](../Topic/bitset::operator%7C=.md)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` inclusiva.|  
|[operator~](../Topic/bitset::operator~.md)|Alterna todos los bits en un `bitset` de destino y devuelve el resultado.|  
  
## Requisitos  
 **Encabezado:** \<bitset\>  
  
 **Espacio de nombres:** std