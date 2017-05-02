---
title: "Platform::Collections::UnorderedMap (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap"
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::UnorderedMap (Clase)
Representa un *mapa* no ordenado, que es una colección de pares clave\-valor.  
  
## Sintaxis  
  
```scr  
template <  
   typename K,  
   typename V,  
   typename C = std::equal_to<K>  
>  
ref class Map sealed;  
```  
  
#### Parámetros  
 `K`  
 Tipo de la clave del par clave\-valor.  
  
 `V`  
 Tipo del valor del par clave\-valor.  
  
 `C`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, es [std::equal\_to\<K\>](../standard-library/equal-to-struct.md).  
  
## Comentarios  
 Los tipos permitidos son:  
  
-   enteros  
  
-   clase de interfaz ^  
  
-   clase ref pública^  
  
-   value struct  
  
-   clase de enumeración pública  
  
 UnorderedMap es básicamente un contenedor de [std::unordered\_map](../standard-library/unordered-map-class.md) que admite el almacenamiento de tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Es la implementación concreta de los tipos [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) e [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) que se pasan a través de las interfaces públicas de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Si intentas usar un tipo Platform::Collections::UnorderedMap en un parámetro o valor devuelto público, se produce el error de compilador C3986. Puedes corregir el error si cambias el tipo del parámetro o el valor devuelto a [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408).  
  
 Para obtener más información, consulta [Colecciones](../cppcx/collections-c-cx.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|UnorderedMap::UnorderedMap \(Constructor\)|Inicializa una nueva instancia de la clase Map.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[UnorderedMap::Clear \(Método\)](../cppcx/unorderedmap-clear-method.md)|Quita todos los pares clave\-valor del objeto Map actual.|  
|[UnorderedMap::First \(Método\)](../cppcx/unorderedmap-first-method.md)|Devuelve un iterador que especifica el primer elemento del objeto Map.|  
|[UnorderedMap::GetView \(Método\)](../cppcx/unorderedmap-getview-method.md)|Devuelve una vista de solo lectura del objeto Map actual; es decir, una clase Platform::Collections::UnorderedMapView.|  
|[UnorderedMap::HasKey \(Método\)](../cppcx/unorderedmap-haskey-method.md)|Determina si el objeto Map actual contiene la clave especificada.|  
|[UnorderedMap::Insert \(Método\)](../cppcx/unorderedmap-insert-method.md)|Agrega el par clave\-valor especificado al objeto Map actual.|  
|[UnorderedMap::Lookup \(Método\)](../cppcx/unorderedmap-lookup-method.md)|Recupera el elemento en la clave especificada del objeto Map actual.|  
|[UnorderedMap::Remove \(Método\)](../cppcx/unorderedmap-remove-method.md)|Elimina el par clave\-valor especificado del objeto Map actual.|  
|[UnorderedMap::Size \(Método\)](../cppcx/unorderedmap-size-method.md)|Devuelve el número de elementos del objeto Map actual.|  
  
### Eventos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[Map::MapChanged \(Evento\)](../cppcx/map-mapchanged-event.md) `event`|Se produce cuando cambia la asignación.|  
  
## Jerarquía de herencia  
 `UnorderedMap`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Platform::Collections \(Espacio de nombres\)](../cppcx/platform-collections-namespace.md)   
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)   
 [Platform::Collections::UnorderedMapView \(Clase\)](../cppcx/platform-collections-unorderedmapview-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)   
 [Crear componentes de Windows en tiempo de ejecución en C\+\+](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)