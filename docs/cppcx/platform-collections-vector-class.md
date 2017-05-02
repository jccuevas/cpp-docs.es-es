---
title: "Platform::Collections::Vector (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector (Clase) (C++/Cx)"
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Platform::Collections::Vector (Clase)
Representa una colección secuencial de objetos a los que se puede tener acceso individualmente por un índice.  
  
## Sintaxis  
  
```  
template <typename T, typename E>  
   ref class Vector sealed;  
```  
  
#### Parámetros  
 `T`  
 Tipo de los elementos contenidos en el objeto Vector.  
  
 `E`  
 Especifica un predicado binario para probar la igualdad con valores de tipo `T`. El valor predeterminado es `std::equal_to<T>`.  
  
## Comentarios  
 Los tipos permitidos son:  
  
1.  enteros  
  
2.  clase de interfaz ^  
  
3.  clase ref pública^  
  
4.  value struct  
  
5.  clase de enumeración pública  
  
 La clase Vector es la implementación concreta de C\+\+ de la interfaz [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410).  
  
 Si intentas usar un tipo Vector en un valor devuelto o parámetro público, se producirá el error del compilador C3986. Puedes corregir el error si cambias el tipo del parámetro o del valor devuelto a [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410). Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Vector::Vector \(Constructor\)](../cppcx/vector-vector-constructor.md)|Inicializa una nueva instancia de la clase Vector.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Vector::Append \(Método\)](../cppcx/vector-append-method.md)|Inserta el elemento especificado a continuación del último elemento en el objeto Vector actual.|  
|[Vector::Clear \(Método\)](../cppcx/vector-clear-method.md)|Elimina todos los elementos del Vector actual.|  
|[Vector::First \(Método\)](../cppcx/vector-first-method.md)|Devuelve un iterador que especifica el primer elemento del objeto Vector.|  
|[Vector::GetAt \(Método\)](../cppcx/vector-getat-method.md)|Recupera el elemento del objeto Vector actual identificado por el índice especificado.|  
|[Vector::GetMany \(Método\)](../cppcx/vector-getmany-method.md)|Recupera una secuencia de elementos del objeto Vector actual, empezando en el índice especificado.|  
|[Vector::GetView \(Método\)](../cppcx/vector-getview-method.md)|Devuelve una vista de solo lectura de una clase Vector; es decir, [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|  
|[Vector::IndexOf \(Método\)](../cppcx/vector-indexof-method.md)|Busca el elemento especificado en el objeto Vector actual y, si lo encuentra, devuelve el índice del elemento.|  
|[Vector::InsertAt \(Método\)](../cppcx/vector-insertat-method.md)|Inserta el elemento especificado en el objeto Vector actual detrás del elemento identificado por el índice especificado.|  
|[Vector::ReplaceAll \(Método\)](../cppcx/vector-replaceall-method.md)|Elimina los elementos del objeto Vector actual y después inserta los elementos de la matriz especificada.|  
|[Vector::RemoveAt \(Método\)](../cppcx/vector-removeat-method.md)|Elimina el elemento identificado por el índice especificado del objeto Vector actual.|  
|[Vector::RemoveAtEnd \(Método\)](../cppcx/vector-removeatend-method.md)|Elimina el elemento al final del objeto Vector actual.|  
|[Vector::SetAt \(Método\)](../cppcx/vector-setat-method.md)|Asigna el valor especificado al elemento del objeto Vector actual identificado por el índice especificado.|  
|[Vector::Size \(Método\)](../cppcx/vector-size-method.md)|Devuelve el número de elementos del objeto Vector actual.|  
  
### Eventos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|evento [Windows::Foundation::Collection::VectorChangedEventHandler\<T\>^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|Se produce cuando cambia el objeto Vector.|  
  
## Jerarquía de herencia  
 `Vector`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Crear componentes de Windows en tiempo de ejecución en C\+\+](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)