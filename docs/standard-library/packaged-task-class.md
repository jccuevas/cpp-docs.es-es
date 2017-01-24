---
title: "packaged_task (Clase) | Microsoft Docs"
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
  - "future/std::packaged_task"
dev_langs: 
  - "C++"
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# packaged_task (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe *un proveedor asincrónico* que es un contenedor de llamada cuya firma de llamada es `Ty(ArgTypes...)`.  Su *estado asincrónica asociada* contiene una copia del objeto accesible además de resultado posible.  
  
## Sintaxis  
  
```  
template<class>  
class packaged_task;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[packaged\_task::packaged\_task \(Constructor\)](../Topic/packaged_task::packaged_task%20Constructor.md)|Construye un objeto `packaged_task`.|  
|[packaged\_task::~packaged\_task \(Destructor\)](../Topic/packaged_task::~packaged_task%20Destructor.md)|Destruye un objeto `packaged_task`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[packaged\_task::get\_future \(Método\)](../Topic/packaged_task::get_future%20Method.md)|Devuelve un objeto de [futuro](../standard-library/future-class.md) que tiene el mismo estado asincrónica asociada.|  
|[packaged\_task::make\_ready\_at\_thread\_exit \(Método\)](../Topic/packaged_task::make_ready_at_thread_exit%20Method.md)|Llama al objeto accesible que se almacena en el estado asincrónica asociada y atómico almacena el valor devuelto.|  
|[packaged\_task::reset \(Método\)](../Topic/packaged_task::reset%20Method.md)|Reemplaza el estado asincrónica asociada.|  
|[packaged\_task::swap \(Método\)](../Topic/packaged_task::swap%20Method.md)|Pase al estado asincrónica asociada al de un objeto especificado.|  
|[packaged\_task::valid \(Método\)](../Topic/packaged_task::valid%20Method.md)|Especifica si el objeto tiene un estado asincrónica asociada.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[packaged\_task::operator\= \(Operador\)](../Topic/packaged_task::operator=%20Operator.md)|Transfiere un estado asincrónica asociado de un objeto especificado.|  
|[packaged\_task::operator\(\) \(Operador\)](../Topic/packaged_task::operator\(\)%20Operator.md)|Llama al objeto accesible que se almacena en el estado asincrónica asociada, atómico almacena el valor devuelto, y establecer el estado *para alistar*.|  
|[packaged\_task::operator bool \(Operador\)](../Topic/packaged_task::operator%20bool%20Operator.md)|Especifica si el objeto tiene un estado asincrónica asociada.|  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)