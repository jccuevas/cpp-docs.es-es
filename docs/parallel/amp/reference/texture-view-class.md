---
title: "texture_view (Clase) | Microsoft Docs"
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
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# texture_view (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Proporciona acceso de lectura y de escritura a una textura.  `texture_view` solo se puede utilizar para leer texturas cuyo tipo de valor es `int`, `unsigned int` o `float` con un valor bpse predeterminado de 32 bits.  Para leer otros formatos de textura, utilice `texture_view<const _Value_type, _Rank>`.  
  
## Sintaxis  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view : public details::_Texture_base<_Value_type, _Rank>;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view<const _Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
```  
  
#### Parámetros  
 `_Value_type`  
 Tipo de los elementos del agregado de texturas.  
  
 `_Rank`  
 El rango de `texture_view`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`value_type`|Tipo de los elementos de los agregados de texturas.|  
|`coordinates_type`|El tipo de la coordenada utilizado para especificar un texel en la `texture_view`, es decir, `short_vector` que tiene el mismo rango que la textura asociada que tiene un tipo de valor de `float`.|  
|`gather_return_type`|El tipo devuelto para operaciones de recopilación, es decir, un rango 4 `short_vector` que mantiene los cuatro componentes de color homogéneos recopilados desde los cuatro valores de texel muestreado.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture\_view::texture\_view \(Constructor\)](../Topic/texture_view::texture_view%20Constructor.md)|Sobrecargado.  Construye una instancia `texture_view`.|  
|[texture\_view::~texture\_view \(Destructor\)](../Topic/texture_view::~texture_view%20Destructor.md)|Destruye la instancia `texture_view`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture\_view::gather\_alpha \(Método\)](../Topic/texture_view::gather_alpha%20Method.md)|Sobrecargado.  Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa \(w\) de los cuatro elementos de textura de ejemplo.|  
|[texture\_view::gather\_blue \(Método\)](../Topic/texture_view::gather_blue%20Method.md)|Sobrecargado.  Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes azul \(z\) de los cuatro elementos de textura de ejemplo.|  
|[texture\_view::gather\_green \(Método\)](../Topic/texture_view::gather_green%20Method.md)|Sobrecargado.  Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes verde \(y\) de los cuatro elementos de textura de ejemplo.|  
|[texture\_view::gather\_red \(Método\)](../Topic/texture_view::gather_red%20Method.md)|Sobrecargado.  Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo \(x\) de los cuatro elementos de textura de ejemplo.|  
|[texture\_view::get \(Método\)](../Topic/texture_view::get%20Method.md)|Sobrecargado.  Obtiene el valor del elemento por su índice.|  
|[texture\_view::sample \(Método\)](../Topic/texture_view::sample%20Method.md)|Sobrecargado.  Muestrea la textura en las coordenadas y el nivel de detalle especificados mediante la configuración de muestreo especificada.|  
|[texture\_view::set \(Método\)](../Topic/texture_view::set%20Method.md)|Establece el valor de un elemento por índice.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture\_view::operator\(\) \(Operador\)](../Topic/texture_view::operator\(\)%20Operator.md)|Sobrecargado.  Obtiene el valor del elemento por su índice.|  
|[texture\_view::operatorOperator](../Topic/texture_view::operatorOperator.md)|Sobrecargado.  Obtiene el valor del elemento por su índice.|  
|[texture\_view::operator\= \(Operador\)](../Topic/texture_view::operator=%20Operator.md)|Sobrecargado.  Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture\_view::value\_type \(Miembro de datos\)](../Topic/texture_view::value_type%20Data%20Member.md)|Tipo de valor de los elementos de `texture_view`.|  
  
## Jerarquía de herencia  
 `_Texture_base`  
  
 `texture_view`  
  
## Requisitos  
 **Encabezado:** amp\_graphics.h  
  
 **Espacio de nombres:** concurrency::graphics  
  
## Vea también  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)