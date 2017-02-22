---
title: "texture (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::texture"
dev_langs: 
  - "C++"
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# texture (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una textura es un agregado de datos en el `accelerator_view` en el dominio de la extensión.  Es una recopilación de variables, una por cada elemento de un dominio de extensión.  Cada variable contiene un valor correspondiente al tipo primitivo de C\+\+ \(`unsigned int`, `int`, `float`, `double`\), un tipo escalar \(`norm`, o `unorm`\) o un tipo de vector corto.  
  
## Sintaxis  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture;  
```  
  
#### Parámetros  
 `_Value_type`  
 Tipo de los elementos de la textura.  
  
 `_Rank`  
 El rango de la textura.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`scalar_type`|Tipos escalares.|  
|`value_type`|Tipos de valor.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture::texture \(Constructor\)](../Topic/texture::texture%20Constructor.md)|Inicializa una nueva instancia de la clase [texture](../../../parallel/amp/reference/texture-class.md).|  
|[texture::~texture \(Destructor\)](../Topic/texture::~texture%20Destructor.md)|Destruye el objeto [texture](../../../parallel/amp/reference/texture-class.md) .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture::copy\_to \(Método\)](../Topic/texture::copy_to%20Method.md)|Copia el objeto [texture](../../../parallel/amp/reference/texture-class.md) en el destino, haciendo una copia en profundidad.|  
|[texture::data \(Método\)](../Topic/texture::data%20Method.md)|Devuelve un puntero de CPU a los datos sin formato de esta textura.|  
|[texture::get \(Método\)](../Topic/texture::get%20Method.md)|Devuelve el valor del elemento en el índice especificado.|  
|[texture::get\_associated\_accelerator\_view \(Método\)](../Topic/texture::get_associated_accelerator_view%20Method.md)|Devuelve el [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|  
|[texture::get\_depth\_pitch \(Método\)](../Topic/texture::get_depth_pitch%20Method.md)|Devuelve el número de bytes entre cada segmento de profundidad en una textura de ensayo de 3D en la CPU.|  
|[texture::get\_row\_pitch \(Método\)](../Topic/texture::get_row_pitch%20Method.md)|Devuelve el número de bytes entre cada fila de en una textura de ensayo de 2D o 3D en la CPU.|  
|[texture::set \(Método\)](../Topic/texture::set%20Method.md)|Establece el valor del elemento en el índice especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture::operator\(\) \(Operador\)](../Topic/texture::operator\(\)%20Operator.md)|Devuelve el valor del elemento especificado por los parámetros.|  
|[texture::operatorOperator](../Topic/texture::operatorOperator.md)|Devuelve el elemento que está en el índice especificado.|  
|[texture::operator\= \(Operador\)](../Topic/texture::operator=%20Operator.md)|Copia el objeto [texture](../../../parallel/amp/reference/texture-class.md) especificado en este.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture::rank \(Constante\)](../Topic/texture::rank%20Constant.md)|Obtiene el rango del objeto de [textura](../../../parallel/amp/reference/texture-class.md).|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture::associated\_accelerator\_view \(Miembro de datos\)](../Topic/texture::associated_accelerator_view%20Data%20Member.md)|Obtiene [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|  
|[texture::depth\_pitch \(Miembro de datos\)](../Topic/texture::depth_pitch%20Data%20Member.md)|Obtiene el número de bytes entre cada segmento de profundidad en una textura de ensayo de 3D en la CPU.|  
|[texture::row\_pitch \(Miembro de datos\)](../Topic/texture::row_pitch%20Data%20Member.md)|Obtiene el número de bytes entre cada fila de en una textura de ensayo de 2D o 3D en la CPU.|  
  
## Jerarquía de herencia  
 `_Texture_base`  
  
 `texture`  
  
## Requisitos  
 **Encabezado:** amp\_graphics.h  
  
 **Espacio de nombres:** Concurrency::graphics  
  
## Vea también  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)