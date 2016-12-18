---
title: "future (Clase) | Microsoft Docs"
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
  - "future/std::future"
dev_langs: 
  - "C++"
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# future (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe *un objeto return asincrónico*.  
  
## Sintaxis  
  
```  
template<class Ty>  
class future;  
```  
  
## Comentarios  
 Cada *proveedor asincrónico* estándar devuelve un objeto cuyo tipo es una instancia de esta plantilla.  Un objeto de `future` proporciona el único acceso al proveedor asincrónico que está asociado a.  Si necesita varios objetos de retorno asincrónico asociados al mismo proveedor asincrónico, copie el objeto de `future` a un objeto de [shared\_future](../standard-library/shared-future-class.md) .  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[future::future \(Constructor\)](../Topic/future::future%20Constructor.md)|Construye un objeto `future`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[future::get \(Método\)](../Topic/future::get%20Method.md)|Recupera el resultado que se almacena en el estado asincrónica asociada.|  
|[future::share \(Método\)](../Topic/future::share%20Method.md)|Convierte el objeto en `shared_future`.|  
|[future::valid \(Método\)](../Topic/future::valid%20Method.md)|Especifica si el objeto no está vacío.|  
|[future::wait \(Método\)](../Topic/future::wait%20Method.md)|Bloquea el subproceso actual hasta que el estado asincrónica asociada está lista.|  
|[future::wait\_for \(Método\)](../Topic/future::wait_for%20Method.md)|Los bloques hasta el estado asincrónica asociada están listos o hasta el tiempo especificado ha transcurrido.|  
|[future::wait\_until \(Método\)](../Topic/future::wait_until%20Method.md)|Los bloques hasta el estado asincrónica asociada están listos o hasta un punto de tiempo especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[future::operator\= \(Operador\)](../Topic/future::operator=%20Operator.md)|Transfiere el estado asincrónica asociado de un objeto especificado.|  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)