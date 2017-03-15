---
title: "type_index (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "typeindex/std::type_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "type_index (clase)"
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# type_index (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de `type_index` contiene un puntero a [type\_info \(Clase\)](../cpp/type-info-class.md) para ayudar en la indización por estos objetos.  
  
```  
class type_index {  
public:  
    type_index(const type_info& tinfo);  
    const char *name() const;  
    size_t hash_code() const;  
    bool operator==(const type_info& right) const;  
    bool operator!=(const type_info& right) const;  
    bool operator<(const type_info& right) const;  
    bool operator<=(const type_info& right) const;  
    bool operator>(const type_info& right) const;  
    bool operator>=(const type_info& right) const;  
};  
```  
  
 El constructor inicializa `ptr` a `&tinfo`.  
  
 `name` devuelve `ptr->name()`.  
  
 `hash_code` devuelve `ptr->hash_code().`  
  
 `operator==` devuelve `*ptr == right.ptr`.  
  
 `operator!=` devuelve `!(*this == right)`.  
  
 `operator<` devuelve `*ptr->before(*right.ptr)`.  
  
 `operator<=` devuelve `!(right < *this).`  
  
 `operator>` devuelve `right < *this`.  
  
 `operator>=` devuelve `!(*this < right)`.  
  
## Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)   
 [\<typeindex\>](../standard-library/typeindex.md)