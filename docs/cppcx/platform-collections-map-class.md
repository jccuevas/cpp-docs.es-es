---
title: "Platform::Collections::Map (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map (Clase) (C++/Cx)"
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: 19
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 19
---
# Platform::Collections::Map (Clase)
Representa una *asignación*, que es una colección de pares clave\-valor.  
  
## Sintaxis  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = std::less<K>  
ref class Map sealed;  
```  
  
#### Parámetros  
 `K`  
 Tipo de la clave del par clave\-valor.  
  
 `V`  
 Tipo del valor del par clave\-valor.  
  
 `C`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std::less\<K\>](../standard-library/less-struct.md).  
  
 \_\_is\_valid\_winrt\_type\(\)  
 Una función generada por el compilador que valida el tipo de K y V y proporciona un mensaje de error descriptivo si el tipo no puede almacenarse en el objeto Map.  
  
## Comentarios  
 Los tipos permitidos son:  
  
-   enteros  
  
-   clase de interfaz ^  
  
-   clase ref pública^  
  
-   value struct  
  
-   clase de enumeración pública  
  
 El objeto Map es básicamente un contenedor de [std::map](../standard-library/map-class.md). Es una implementación concreta en C\+\+ de los tipos [Windows::Foundation::Collections::IMap\<Windows::Foundation::Collections::IKeyValuePair\<K,V\>\>](http://go.microsoft.com/fwlink/p/?LinkId=262408) e [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) que se pasan a las interfaces de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] públicas. Si intentas usar un tipo `Platform::Collections::Map` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error si cambia el tipo del parámetro o el valor devuelto a [Windows::Foundation::Collections::IMap\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262408).  
  
 Para obtener más información, consulta [Colecciones](../cppcx/collections-c-cx.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Map::Map \(Constructor\)](../cppcx/map-map-constructor.md)|Inicializa una nueva instancia de la clase Map.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Map::Clear \(Método\)](../cppcx/map-clear-method.md)|Quita todos los pares clave\-valor del objeto Map actual.|  
|[Map::First \(Método\)](../cppcx/map-first-method.md)|Devuelve un iterador que especifica el primer elemento del objeto Map.|  
|[Map::GetView \(Método\)](../cppcx/map-getview-method.md)|Devuelve una vista de solo lectura del objeto Map actual; es decir, [Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md).|  
|[Map::HasKey \(Método\)](../cppcx/map-haskey-method.md)|Determina si el objeto Map actual contiene la clave especificada.|  
|[Map::Insert \(Método\)](../cppcx/map-insert-method.md)|Agrega el par clave\-valor especificado al objeto Map actual.|  
|[Map::Lookup \(Método\)](../cppcx/map-lookup-method.md)|Recupera el elemento en la clave especificada del objeto Map actual.|  
|[Map::Remove \(Método\)](../cppcx/map-remove-method.md)|Elimina el par clave\-valor especificado del objeto Map actual.|  
|[Map::Size \(Método\)](../cppcx/map-size-method.md)|Devuelve el número de elementos del objeto Map actual.|  
  
### Eventos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[Map::MapChanged \(Evento\)](../cppcx/map-mapchanged-event.md) `event`|Se produce cuando cambia la asignación.|  
  
## Jerarquía de herencia  
 `Map`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)