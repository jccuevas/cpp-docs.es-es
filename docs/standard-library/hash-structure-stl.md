---
title: "hash (Estructura, STL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "thread/std::hash"
dev_langs: 
  - "C++"
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# hash (Estructura, STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define una función miembro que devuelve un valor que se determina de forma única por `Val`. Define la función miembro un [hash](hash%20Class.md) función que es adecuado para los valores de asignación de tipo `thread::id` a una distribución de valores de índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** subproceso  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\< subproceso>](../standard-library/thread.md)   
 [unary_function (struct)](../standard-library/unary-function-struct.md)
