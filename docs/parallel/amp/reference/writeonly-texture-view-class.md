---
title: "writeonly_texture_view (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::writeonly_texture_view"
dev_langs: 
  - "C++"
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# writeonly_texture_view (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Proporciona acceso de solo escritura a una textura.  
  
## Sintaxis  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view<_Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
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
|`scalar_type`||  
|`value_type`|Tipo de los elementos de la textura.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[writeonly\_texture\_view::writeonly\_texture\_view \(Constructor\)](../Topic/writeonly_texture_view::writeonly_texture_view%20Constructor.md)|Inicializa una nueva instancia de la clase [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md).|  
|[writeonly\_texture\_view::~writeonly\_texture\_view \(Destructor\)](../Topic/writeonly_texture_view::~writeonly_texture_view%20Destructor.md)|Destruye el objeto [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md).|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[writeonly\_texture\_view::set \(Método\)](../Topic/writeonly_texture_view::set%20Method.md)|Establece el valor del elemento en el índice especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[writeonly\_texture\_view::operator\= \(Operador\)](../Topic/writeonly_texture_view::operator=%20Operator.md)|Copia el objeto especificado [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) en este otro.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[writeonly\_texture\_view::rank \(Constante\)](../Topic/writeonly_texture_view::rank%20Constant.md)|Obtiene el rango del objeto [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md).|  
  
## Jerarquía de herencia  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## Requisitos  
 **Encabezado:** amp\_graphics.h  
  
 **Espacio de nombres:** Concurrency::graphics  
  
## Vea también  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)