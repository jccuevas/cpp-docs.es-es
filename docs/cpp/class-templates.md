---
title: "Plantillas de clase | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de clase"
  - "clases [C++], funcionamiento en tipo"
  - "plantillas, plantillas de clase"
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Plantillas de clase
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar plantillas de clase para crear una familia de clases que operen en un tipo.  Las plantillas de clase son tipos parametrizados.  Permiten crear una clase distinta para cada valor plausible de los parámetros pasados \(denominados argumentos de plantilla\).  
  
 Los argumentos de plantilla pueden ser tipos o valores constantes de un tipo especificado.  Por ejemplo:  
  
```  
// class_templates.cpp  
template <class T, int i> class TempClass   
{  
public:  
    TempClass( void );  
    ~TempClass( void );  
    int MemberSet( T a, int b );  
private:  
    T Tarray[i];  
    int arraysize;  
};  
  
int main()  
{  
}  
```  
  
 En este ejemplo, la clase con plantilla utiliza dos parámetros, un tipo `T` y un int `i`.  Al parámetro `T` se le puede pasar cualquier tipo, incluidas estructuras y clases.  Al parámetro `i` se le debe pasar una constante entera.  Como `i` es una constante definida en tiempo de compilación, puede definir una matriz de miembros de tamaño `i` mediante una declaración de matriz estándar.  
  
 Para obtener más información, vea:  
  
-   [Miembros de plantillas de clase](../Topic/Members%20of%20Class%20Templates.md)  
  
-   [Plantillas para miembros de clase](../Topic/Templates%20for%20Class%20Members.md)  
  
-   [Funciones miembro de clases de plantilla](../Topic/Member%20Functions%20of%20Template%20Classes.md)  
  
-   [Plantillas de clase anidadas](../Topic/Nested%20Class%20Templates.md)  
  
-   [Creación de instancias de una plantilla de clase](../Topic/Class%20Template%20Instantiation.md)  
  
-   [Especialización explícita de las plantillas de clase](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)  
  
-   [Especialización parcial de plantillas de clase](../cpp/template-specialization-cpp.md)  
  
-   [Argumentos predeterminados para plantillas de clase](../Topic/Default%20Arguments%20for%20Class%20Templates.md)  
  
-   [Friends de plantilla](../cpp/template-friends.md)  
  
## Vea también  
 [Plantillas](../cpp/templates-cpp.md)