---
title: "codecvt_base (Clase) | Microsoft Docs"
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
  - "codecvt_base"
  - "xlocale/std::codecvt_base"
  - "std.codecvt_base"
  - "std::codecvt_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_base (clase)"
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase base para la clase de codecvt que se utiliza para definir un tipo de enumeración referencia como **resultado**, utilizada como el tipo de valor devuelto para el miembro de la faceta funciona para indicar el resultado de una conversión.  
  
## Sintaxis  
  
```  
class codecvt_base : public locale::facet {  
public:  
    enum result {ok, partial, error, noconv};  
    codecvt_base(  
        size_t _Refs = 0  
);  
    bool always_noconv() const;  
    int max_length() const;  
    int encoding() const;  
    ~codecvt_base()  
protected:  
    virtual bool do_always_noconv() const;  
    virtual int do_max_length() const;  
    virtual int do_encoding() const;  
};  
```  
  
## Comentarios  
 La clase describe un común de enumeración a todas las especializaciones de la clase de plantilla [codecvt](../standard-library/codecvt-class.md).  El resultado de la enumeración describe los valores devueltos posibles de [do\_in](../Topic/codecvt::do_in.md) o de [do\_out](../Topic/codecvt::do_out.md):  
  
-   **aceptar** si la conversión entre las codificaciones de caracteres internas y externas correctamente.  
  
-   **partial** si el destino no es suficientemente grande para que la conversión se realiza correctamente.  
  
-   **ERROR** si la secuencia de origen es incorrecta.  
  
-   **noconv** si la función no realiza ninguna conversión.  
  
## Requisitos  
 Configuración regional \<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)