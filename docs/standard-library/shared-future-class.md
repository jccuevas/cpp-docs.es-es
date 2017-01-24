---
title: "shared_future (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::shared_future"
dev_langs: 
  - "C++"
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shared_future (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe *un objeto return asincrónico*.  Al contrario del objeto de [futuro](../standard-library/future-class.md) , *un proveedor asincrónico* se puede asociar a cualquier número de objetos de `shared_future` .  
  
## Sintaxis  
  
```  
template<class Ty>  
class shared_future;  
```  
  
## Comentarios  
 No llame a ningún método distinto de `valid`, de `operator=`, y del destructor en un objeto de `shared_future` que está *vacío*.  
  
 los objetos de`shared_future` no se sincronizan.  Llamar a métodos en el mismo objeto de varios subprocesos presenta una precipitan de datos que tiene resultados imprevisibles.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[shared\_future::shared\_future \(Constructor\)](../Topic/shared_future::shared_future%20Constructor.md)|Construye un objeto `shared_future`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[shared\_future::get \(Método\)](../Topic/shared_future::get%20Method.md)|Recupera el resultado que se almacena en *el estado asincrónica asociada*.|  
|[shared\_future::valid \(Método\)](../Topic/shared_future::valid%20Method.md)|Especifica si el objeto no está vacío.|  
|[shared\_future::wait \(Método\)](../Topic/shared_future::wait%20Method.md)|Bloquea el subproceso actual hasta que el estado asincrónica asociada está lista.|  
|[shared\_future::wait\_for \(Método\)](../Topic/shared_future::wait_for%20Method.md)|Los bloques hasta el estado asincrónica asociada están listos o hasta el tiempo especificado ha transcurrido.|  
|[shared\_future::wait\_until \(Método\)](../Topic/shared_future::wait_until%20Method.md)|Los bloques hasta el estado asincrónica asociada están listos o hasta un punto de tiempo especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[shared\_future::operator\= \(Operador\)](../Topic/shared_future::operator=%20Operator.md)|Asigna un nuevo estado asincrónica asociada.|  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)