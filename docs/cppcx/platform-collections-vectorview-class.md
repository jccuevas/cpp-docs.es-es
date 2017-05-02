---
title: "Platform::Collections::VectorView (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView (Clase)"
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Platform::Collections::VectorView (Clase)
Representa una vista de solo lectura de una colección secuencial de objetos a los que se puede obtener acceso individualmente por índice. El parámetro de plantilla especifica el tipo de cada objeto de la colección.  
  
## Sintaxis  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### Parámetros  
 `T`  
 El tipo de los elementos contenidos en el objeto `VectorView`.  
  
 `E`  
 Especifica un predicado binario para probar la igualdad con valores de tipo `T`. El valor predeterminado es `std::equal_to<T>`.  
  
## Comentarios  
 La clase `VectorView` implementa la interfaz [Windows::Foundation::Collections::IVectorView\<T\>](http://go.microsoft.com/fwlink/p/?LinkId=262411) y compatibilidad con los iteradores de la Biblioteca de plantillas estándar.  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorView::VectorView \(Constructor\)](../cppcx/vectorview-vectorview-constructor.md)|Inicializa una nueva instancia de la clase VectorView.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorView::First \(Método\)](../cppcx/vectorview-first-method.md)|Devuelve un iterador que especifica el primer elemento del objeto VectorView.|  
|[VectorView::GetAt \(Método\)](../cppcx/vectorview-getat-method.md)|Recupera el elemento del objeto VectorView actual indicado por el índice especificado.|  
|[VectorView::GetMany \(Método\)](../cppcx/vectorview-getmany-method.md)|Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.|  
|[VectorView::IndexOf \(Método\)](../cppcx/vectorview-indexof-method.md)|Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.|  
|[VectorView::Size \(Método\)](../cppcx/vectorview-size-method.md)|Devuelve el número de elementos del objeto VectorView actual.|  
  
## Jerarquía de herencia  
 `VectorView`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Crear componentes de Windows en tiempo de ejecución en C\+\+](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)