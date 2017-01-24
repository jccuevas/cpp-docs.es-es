---
title: "basic_iostream (Clase) | Microsoft Docs"
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
  - "istream/std::basic_iostream"
  - "std.basic_iostream"
  - "basic_iostream"
  - "std::basic_iostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_iostream (clase)"
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 22
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_iostream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_iostream : public basic_istream<Elem, Tr>,  
        public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr> *_Strbuf);  
    virtual ~basic_iostream();  
};  
```  
  
## Comentarios  
 La clase de plantilla describe un objeto que controla las inserciones a través de su clase base [basic\_ostream](../standard-library/basic-ostream-class.md)\<`Elem`, `Tr`\> y las extracciones a través de su clase base [basic\_istream](../standard-library/basic-istream-class.md)\<`Elem`, `Tr`\>.  Los dos objetos comparten una clase base virtual común [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, `Tr`\>.  También administran un búfer de secuencia común, con elementos de tipo `Elem`, cuyos rasgos de caracteres vienen determinados por la clase `Tr`.  El constructor inicializa sus clases base a través de `basic_istream`\(**strbuf**\) y `basic_ostream`\(**strbuf**\).  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_iostream](../Topic/basic_iostream::basic_iostream.md)|Crear un objeto `basic_iostream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[swap](../Topic/basic_iostream::swap.md)|Intercambia el contenido del objeto `basic_iostream` proporcionado con el contenido de este objeto.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/basic_iostream::operator=.md)|Asigna el valor de un objeto `basic_iostream` especificado a este objeto.  Se trata de una asignación de movimiento que implica un `rvalue` que no deja ninguna copia atrás.|  
  
## Requisitos  
 **Encabezado:** \<istream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)