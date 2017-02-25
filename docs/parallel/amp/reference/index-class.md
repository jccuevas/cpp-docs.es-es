---
title: "index (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estructura del índice"
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# index (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Define un punto de índice *N*\-dimensional.  
  
## Sintaxis  
  
```  
template <  
   int _Rank  
>  
class index;  
```  
  
#### Parámetros  
 `_Rank`  
 El rango o número de dimensiones.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[index::index \(Constructor\)](../Topic/index::index%20Constructor.md)|Inicializa una nueva instancia de la clase `index`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[index::operator\-\- \(Operador\)](../Topic/index::operator--%20Operator.md)|Reduce cada elemento del objeto `index`.|  
|[index::operator\(mod\)\= \(Operador\)](../Topic/index::operator\(mod\)=%20Operator.md)|Calcula el módulo \(residuo\) de cada elemento del objeto `index` cuando este elemento se divide por un número.|  
|[index::operator\*\= \(Operador\)](../Topic/index::operator*=%20Operator.md)|Multiplica cada elemento del objeto `index` por un número.|  
|[index::operator\/\= \(Operador\)](../Topic/index::operator-=%20Operator2.md)|Divide cada elemento del objeto `index` por un número.|  
|[index::operatorOperator](../Topic/index::operatorOperator.md)|Devuelve el elemento que está en el índice especificado.|  
|[index::operator\+\+ \(Operador\)](../Topic/index::operator++%20Operator.md)|Incrementa cada elemento del objeto `index`.|  
|[index::operator\+\= \(Operador\)](../Topic/index::operator+=%20Operator.md)|Agrega el número especificado a cada elemento del objeto `index`.|  
|[index::operator\= \(Operador\)](../Topic/index::operator=%20Operator.md)|Copia el contenido del objeto especificado `index` en este.|  
|[index::operator\-\= \(Operador\)](../Topic/index::operator-=%20Operator1.md)|Resta el número especificado de cada elemento del objeto `index`.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[index::rank \(Constante\)](../Topic/index::rank%20Constant.md)|Almacena el rango del objeto `index`.|  
  
## Jerarquía de herencia  
 `index`  
  
## Comentarios  
 La estructura `index` representa un vector de coordenadas de *N* enteros que especifica una posición única en un espacio *N* dimensional.  Los valores del vector se ordenan del más significativo al menos significativo.  Puede recuperar los valores de los componentes mediante [index::operator\= \(Operador\)](../Topic/index::operator=%20Operator.md).  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)