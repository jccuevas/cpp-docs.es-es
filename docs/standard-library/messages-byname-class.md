---
title: "messages_byname (Clase) | Microsoft Docs"
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
  - "messages_byname"
  - "std::messages_byname"
  - "std.messages_byname"
  - "xlocmes/std::messages_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_byname (clase)"
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla derivada describe un objeto que puede actuar como faceta de mensajes de una configuración regional, lo que permite la recuperación de mensajes adaptados.  
  
## Sintaxis  
  
```  
template<class CharType>  
    class messages_byname : public messages<CharType> {  
public:  
    explicit messages_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit messages_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~messages_byname();  
};  
```  
  
#### Parámetros  
 `_Locname`  
 Una configuración regional denominada.  
  
 `_Refs`  
 Un recuento inicial de referencia.  
  
## Comentarios  
 Su comportamiento es determinado por la configuración regional denominada `_Locname`.  Cada constructor inicializa el objeto base con [mensajes](../Topic/messages::messages.md)\<CharType\>\(`_Refs`\).  
  
## Requisitos  
 configuración regional \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)