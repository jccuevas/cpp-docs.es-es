---
title: "messages_base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.messages_base"
  - "messages_base"
  - "std::messages_base"
  - "locale/std::messages_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_base (clase)"
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# messages_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase base describe `int` escrito para el catálogo de mensajes.  
  
## Sintaxis  
  
```  
struct messages_base : locale::facet {  
    typedef int catalog;  
    explicit messages_base(size_t _Refs = 0)  
};  
```  
  
## Comentarios  
 El catálogo de tipo es un sinónimo de `int` tipo que describe los valores devueltos posibles de messages::[do\_open](../Topic/messages::do_open.md).  
  
## Requisitos  
 Configuración regional \<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)