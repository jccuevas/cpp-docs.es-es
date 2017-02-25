---
title: "numpunct_byname (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.numpunct_byname"
  - "numpunct_byname"
  - "xlocnum/std::numpunct_byname"
  - "std::numpunct_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numpunct_byname (clase)"
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# numpunct_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla derivada describe un objeto que puede actuar como faceta de `numpunct` de una configuración regional habilitando el formato y la puntuación de expresiones numéricas y boolean.  
  
## Sintaxis  
  
```  
template<Class CharType>  
    class numpunct_byname : public numpunct<Elem> {  
public:  
    explicit numpunct_byname(  
        const char* _Locname,  
        size_t _Refs = 0  
    );  
    explicit numpunct_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~numpunct_byname( );  
   };  
```  
  
## Comentarios  
 Su comportamiento es determinado por la configuración regional `_Locname`de [denominado](../Topic/locale::name.md) .  El constructor inicializa el objeto base con [numpunct](../Topic/numpunct::numpunct.md)\<CharType\>\(`_Refs`\).  
  
## Requisitos  
 configuración regional \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)