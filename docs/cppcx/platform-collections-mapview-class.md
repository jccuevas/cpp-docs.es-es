---
title: "Platform::Collections::MapView (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView (Clase)"
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Collections::MapView (Clase)
Representa una vista de solo lectura en un *mapa*, que es una colección de pares clave\-valor.  
  
## Sintaxis  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>  
>  
ref class MapView sealed;  
```  
  
#### Parámetros  
 `K`  
 Tipo de la clave del par clave\-valor.  
  
 `V`  
 Tipo del valor del par clave\-valor.  
  
 `C`  
 Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView. De forma predeterminada, es [::std::less\<K\>](../standard-library/less-struct.md).  
  
## Comentarios  
 MapView es la implementación concreta en C\+\+ de la interfaz [Windows::Foundation::Collections::IMapView \<K,V](http://go.microsoft.com/fwlink/p/?LinkId=262409) que se pasa a través de la interfaz binaria de aplicación \(ABI\). Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[MapView::MapView \(Constructor\)](../cppcx/mapview-mapview-constructor.md)|Inicializa una nueva instancia de la clase MapView.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[MapView::First \(Método\)](../cppcx/mapview-first-method.md)|Devuelve un iterador que se inicializa el primer elemento en la vista de mapa.|  
|[MapView::HasKey \(Método\)](../cppcx/mapview-haskey-method.md)|Determina si el objeto MapView actual contiene la clave especificada.|  
|[MapView::Lookup \(Método\)](../cppcx/mapview-lookup-method.md)|Recupera el elemento en la clave especificada del objeto MapView actual.|  
|[MapView::Size \(Método\)](../cppcx/mapview-size-method.md)|Devuelve el número de elementos del objeto MapView actual.|  
|[MapView::Split \(Método\)](../cppcx/mapview-split-method.md)|Divide un objeto MapView original en dos objetos MapView.|  
  
## Jerarquía de herencia  
 `MapView`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)