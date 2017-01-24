---
title: "codecvt_byname (Clase) | Microsoft Docs"
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
  - "std.codecvt_byname"
  - "codecvt_byname"
  - "std::codecvt_byname"
  - "xlocale/std::codecvt_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_byname (clase)"
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla derivada que describe un objeto que puede actuar como faceta collate de una configuración regional, lo que permite la recuperación de información específica de un área cultural pertenecientes a conversiones.  
  
## Sintaxis  
  
```  
template<Class CharType, class Byte, class StateType>  
    class codecvt_byname: public codecvt<CharType, Byte, StateType> {  
public:  
    explicit codecvt_byname(  
        const char* _Locname,  
        size_t _Refs = 0  
    );  
```  
  
```  
explicit codecvt_byname(  
    const string& _Locname,  
    size_t _Refs = 0  
);  
```  
  
```  
protected:  
    virtual ~codecvt_byname( );  
};  
```  
  
#### Parámetros  
 `_Locname`  
 Una configuración regional denominada.  
  
 `_Refs`  
 Un recuento inicial de referencia.  
  
## Comentarios  
 Las facetas de Byname se crean automáticamente cuando se construye una configuración regional denominada.  
  
 Su comportamiento es determinado por la configuración regional denominada `_Locname`.  Cada constructor inicializa el objeto base con [codecvt](../standard-library/codecvt-class.md)\<CharType, byte, StateType\>\(`_Refs`\).  
  
## Requisitos  
 configuración regional \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)