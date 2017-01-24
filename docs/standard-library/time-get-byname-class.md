---
title: "time_get_byname (Clase) | Microsoft Docs"
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
  - "std.time_get_byname"
  - "time_get_byname"
  - "xloctime/std::time_get_byname"
  - "std::time_get_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_get_byname (clase)"
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
caps.latest.revision: 25
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_get_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla derivada describe un objeto que puede actuar como faceta de configuración regional de `time_get`tipo\<CharType, InputIterator\>.  
  
## Sintaxis  
  
```  
template<class Elem, class InputIterator =   
   istreambuf_iterator<CharType, char_traits<CharType> > >  
   class time_get_byname : public time_get<CharType, InputIterator>  
{  
public:  
    explicit time_get_byname(  
        const char *_Locname,  
         size_t _Refs = 0  
    );  
    explicit time_get_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~time_get_byname()  
};  
```  
  
#### Parámetros  
 `_Locname`  
 Una configuración regional denominada.  
  
 `_Refs`  
 Un recuento inicial de referencia.  
  
## Requisitos  
 Su comportamiento es determinado por la configuración regional denominada `_Locname`.  Cada constructor inicializa el objeto base con [time\_get](../Topic/time_get::time_get.md)\<CharType, InputIterator\>\(`_Refs`\).  
  
## Requisitos  
 configuración regional \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)