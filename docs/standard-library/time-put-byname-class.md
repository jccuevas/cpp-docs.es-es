---
title: "time_put_byname (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "time_put_byname"
  - "xloctime/std::time_put_byname"
  - "std.time_put_byname"
  - "std::time_put_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put_byname (clase)"
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# time_put_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase derivada de plantilla describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_put`\< CharType, OutputIterator \>.  
  
## Sintaxis  
  
```  
template<class CharType,  
 class OutIt = ostreambuf_iterator<CharType, char_traits<CharType> > >  
 class time_put_byname : public time_put<CharType, OutputIterator>  
{  
public:  
    explicit time_put_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit time_put_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~time_put_byname();  
};  
```  
  
#### Parámetros  
 `_Locname`  
 Un nombre de configuración regional.  
  
 `_Refs`  
 Un recuento de referencia inicial.  
  
## Comentarios  
 Su comportamiento viene determinado por la [denominado](../Topic/locale::name.md) configuración regional `_Locname`. Cada constructor inicializa su objeto base con [time\_put](../Topic/time_put::time_put.md)\< CharType, OutputIterator \> \(`_Refs`\).  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)