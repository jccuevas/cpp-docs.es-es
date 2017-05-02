---
title: "Platform::Collections (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Collections (Espacio de nombres)"
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Collections (Espacio de nombres)
El espacio de nombres Platform::Collection contiene las clases `Map`, `MapView`, `Vector` y `VectorView`. Estas clases son implementaciones concretas de las interfaces correspondientes que se definen en el espacio de nombres [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645). Los tipos de colección concretos no son portátiles a través de la ABI \(por ejemplo, cuando un programa de JavaScript o de C\# llama a un componente de C\+\+\), pero se pueden convertir implícitamente a sus tipos de interfaz correspondientes. Por ejemplo, si implementa un método público que rellena y devuelve una colección, use [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) para implementar la colección internamente y usa [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) como tipo de valor devuelto. Para obtener más información, consulte [Colecciones](../cppcx/collections-c-cx.md) y [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf).  
  
 Puedes crear un objeto Platform::Collections::Vector a partir de un objeto [std::vector](../Topic/vector%20Class%201.md) y un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) a partir de un objeto [std::map](../standard-library/map-class.md).  
  
 Además, el espacio de nombres Platform::Collection proporciona compatibilidad para la nueva inserción y especificación de iteradores, así como los iteradores `Vector` y `VectorView`.  
  
 Debes incluir \(`#include`\) el encabezado collection.h para utilizar los tipos en el espacio de nombres Platform::Collection.  
  
## Sintaxis  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collection;  
```  
  
## Miembros  
 Este espacio de nombres contiene los miembros siguientes.  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Platform::Collections::BackInsertIterator \(Clase\)](../cppcx/platform-collections-backinsertiterator-class.md)|Representa un iterador que inserta un elemento al final de una colección.|  
|[Platform::Collections::InputIterator \(Clase\)](../cppcx/platform-collections-inputiterator-class.md)|Representa un iterador que inserta un elemento al principio de una colección.|  
|[Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)|Representa una colección modificable de pares clave\-valor a los que se tiene acceso mediante una clave. Similar a [std::map](../standard-library/map-class.md).|  
|[Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md)|Representa una colección de solo lectura de pares clave\-valor a los que se tiene acceso mediante una clave.|  
|[Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)|Representa una secuencia modificable de elementos. Similar a [std::vector](../Topic/vector%20Class%201.md).|  
|[Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)|Representa un iterador que recorre una colección de `Vector`.|  
|[Platform::Collections::VectorView \(Clase\)](../cppcx/platform-collections-vectorview-class.md)|Representa una secuencia de solo lectura de elementos.|  
|[Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)|Representa un iterador que recorre una colección de `VectorView`.|  
  
## Jerarquía de herencia  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)  
  
## Requisitos  
 **Metadatos:** platform.winmd  
  
 **Espacio de nombres:** Platform::Collections  
  
 **Opción del compilador:** \/ZW  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)