---
title: "Platform::Collections::UnorderedMapView (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView"
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::Collections::UnorderedMapView (Clase)
Representa una vista de solo lectura en un *mapa*, que es una colección de pares clave\-valor.  
  
## Sintaxis  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>  
>  
ref class UnorderedMapView sealed;  
```  
  
#### Parámetros  
 `K`  
 Tipo de la clave del par clave\-valor.  
  
 `V`  
 Tipo del valor del par clave\-valor.  
  
 `C`  
 Un tipo que proporciona un objeto de función que puede comparar dos valores de clave para determinar si son iguales. De forma predeterminada, es [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)  
  
## Comentarios  
 UnorderedMapView es la implementación concreta en C\+\+ de la interfaz [Windows::Foundation::Collections::IMapView\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262409) que se pasa a través de la interfaz binaria de aplicación \(ABI\). Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[UnorderedMapView::UnorderedMapView \(Constructor\)](../cppcx/unorderedmapview-unorderedmapview-constructor.md)|Inicializa una nueva instancia de la clase UnorderedMapView.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[UnorderedMapView::First \(Método\)](../cppcx/unorderedmapview-first-method.md)|Devuelve un iterador que se inicializa el primer elemento en la vista de mapa.|  
|[UnorderedMapView::HasKey \(Método\)](../cppcx/unorderedmapview-haskey-method.md)|Determina si el objeto UnorderedMapView actual contiene la clave especificada.|  
|[UnorderedMapView::Lookup \(Método\)](../cppcx/unorderedmapview-lookup-method.md)|Recupera el elemento en la clave especificada del objeto UnorderedMapView actual.|  
|[UnorderedMapView::Size \(Método\)](../cppcx/unorderedmapview-size-method.md)|Devuelve el número de elementos del objeto UnorderedMapView actual.|  
|[UnorderedMapView::Split \(Método\)](../cppcx/unorderedmapview-split-method.md)|Divide un objeto UnorderedMapView original en dos objetos UnorderedMapView.|  
  
## Jerarquía de herencia  
 `UnorderedMapView`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections \(Espacio de nombres\)](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](http://go.microsoft.com/fwlink/p/?LinkId=262409)