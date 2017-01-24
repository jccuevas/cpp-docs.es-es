---
title: "range_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter (clase) [STL/CLR]"
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla que contiene un par de iteradores que se utilizan para implementar varias interfaces de \(BCL\) de la biblioteca de clases base.  Utiliza el range\_adapter para manipular un intervalo de STL\/CLR como si fuera una colección de BCL.  
  
## Sintaxis  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### Parámetros  
 Iter  
 El tipo asociado a los iteradores ajustados.  
  
## Miembros  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[range\_adapter::range\_adapter](../dotnet/range-adapter-range-adapter-stl-clr.md)|Construye un objeto de adaptador.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[range\_adapter::operator\=](../dotnet/range-adapter-operator-assign-stl-clr.md)|Reemplaza los pares almacenados de iterador.|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Recorre en iteración los elementos de la colección.|  
|<xref:System.Collections.ICollection>|Mantiene un grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Recorre en iteración de elementos escritos en la colección.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantiene un grupo de elementos escritos.|  
  
## Comentarios  
 El range\_adapter almacena un par de iteradores, que a su vez delimitan una secuencia de elementos.  El objeto implementa cuatro interfaces de BCL que permiten recorrer en iteración los elementos, en orden.  Utiliza esta clase de plantilla para manipular intervalos de STL\/CLR como contenedores de BCL.  
  
## Requisitos  
 cliext \<\/adaptador de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)