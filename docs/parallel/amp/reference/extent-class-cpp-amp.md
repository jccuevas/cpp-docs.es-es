---
title: "extent (Clase) (C++ AMP) | Microsoft Docs"
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
  - "amp/Concurrency::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent (estructura)"
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# extent (Clase) (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa un vector de valores enteros de *N* que especifican los límites de un espacio dimensional *N* que tiene un origen de 0.  Los valores del vector se ordenan del más significativo al menos significativo.  
  
## Sintaxis  
  
```  
template <  
   int _Rank>  
class extent;  
```  
  
#### Parámetros  
 `_Rank`  
 El rango del objeto `extent`.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[extent::extent \(Constructor\)](../Topic/extent::extent%20Constructor.md)|Inicializa una nueva instancia de la clase `extent`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[extent::contains \(Método\)](../Topic/extent::contains%20Method.md)|Comprueba que el objeto especificado `extent` tiene el rango especificado.|  
|[extent::size \(Método\)](../Topic/extent::size%20Method.md)|Devuelve el tamaño lineal total de la extensión \(en unidades de elementos\).|  
|[extent::tile \(Método\)](../Topic/extent::tile%20Method.md)|Genera un objeto `tiled_extent` con extensiones de mosaico proporcionadas por las dimensiones especificadas.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[extent::operator\- \(Operador\)](../Topic/extent::operator-%20Operator.md)|Devuelve un nuevo objeto `extent` creado al restar los elementos de `index` de los elementos correspondientes de `extent`.|  
|[extent::operator\-\- \(Operador\)](../Topic/extent::operator--%20Operator.md)|Reduce cada elemento del objeto `extent`.|  
|[extent::operator\(mod\)\= \(Operador\)](../Topic/extent::operator\(mod\)=%20Operator.md)|Calcula el módulo \(residuo\) de cada elemento del objeto `extent` cuando este elemento se divide por un número.|  
|[extent::operator\*\= \(Operador\)](../Topic/extent::operator*=%20Operator.md)|Multiplica cada elemento del objeto `extent` por un número.|  
|[extent::operator\/\= \(Operador\)](../Topic/extent::operator-=%20Operator1.md)|Divide cada elemento del objeto `extent` por un número.|  
|[extent::operatorOperator](../Topic/extent::operatorOperator.md)|Devuelve el elemento que está en el índice especificado.|  
|[extent::operator\+ \(Operador\)](../Topic/extent::operator+%20Operator.md)|Devuelve un nuevo objeto `extent` creado al agregar los correspondientes elementos `index` y `extent`.|  
|[extent::operator\+\+ \(Operador\)](../Topic/extent::operator++%20Operator.md)|Incrementa cada elemento del objeto `extent`.|  
|[extent::operator\+\= \(Operador\)](../Topic/extent::operator+=%20Operator.md)|Agrega el número especificado a cada elemento del objeto `extent`.|  
|[extent::operator\= \(Operador\)](../Topic/extent::operator=%20Operator.md)|Copia el contenido de otro objeto `extent` en este.|  
|[extent::operator\-\= \(Operador\)](../Topic/extent::operator-=%20Operator2.md)|Resta el número especificado de cada elemento del objeto `extent`.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[extent::rank \(Constante\)](../Topic/extent::rank%20Constant.md)|Obtiene el rango del objeto `extent`.|  
  
## Jerarquía de herencia  
 `extent`  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)