---
title: "moneypunct_byname (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.moneypunct_byname"
  - "std::moneypunct_byname"
  - "xlocmon/std::moneypunct_byname"
  - "moneypunct_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct_byname (clase)"
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# moneypunct_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla derivada que describe un objeto que puede actuar como faceta de `moneypunct` de una configuración regional, habilitando el campo de entrada monetario de formato o campos monetarios de salida.  
  
## Sintaxis  
  
```  
template<class CharType, bool Intl = false>  
class moneypunct_byname : public moneypunct<CharType, Intl>  
{  
public:  
    explicit moneypunct_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit moneypunct_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~moneypunct_byname();  
};  
```  
  
## Comentarios  
 Su comportamiento es determinado por la configuración regional denominada `_Locname`.  Cada constructor inicializa el objeto base con [moneypunct](../Topic/moneypunct::moneypunct.md)\<CharType, Internacionales\>\(`_Refs`\).  
  
## Requisitos  
 configuración regional \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)