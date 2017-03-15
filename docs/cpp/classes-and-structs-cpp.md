---
title: "Clases y structs (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++]"
  - "estructuras , clases de C++"
  - "tipos definidos por el usuario"
  - "tipos definidos por el usuario, clases de C++"
  - "Visual C++, clases"
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases y structs (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En esta sección se presentan las clases y structs de C\+\+.  Las dos construcciones son idénticas en C\+\+, salvo que, en los structs, la accesibilidad predeterminada es pública, mientras que en las clases es privada.  
  
```  
  
```  
  
 Las clases y los structs son las construcciones con las que define sus propios tipos.  Las clases y los structs pueden contener miembros de datos y funciones miembro, lo que permite describir el comportamiento y el estado del tipo.  
  
 Se incluyen los temas siguientes:  
  
-   [class](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Información general sobre miembros de clase](../cpp/class-member-overview.md)  
  
-   [Control de acceso a miembros](../cpp/member-access-control-cpp.md)  
  
-   [Herencia](../cpp/inheritance-cpp.md)  
  
-   [Miembros estáticos](../cpp/static-members-cpp.md)  
  
-   [Conversiones](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [Miembros de datos mutables \(especificador mutable\)](../cpp/mutable-data-members-cpp.md)  
  
-   [Declaraciones de clase anidadas](../cpp/nested-class-declarations.md)  
  
-   [Tipos de clase anónima](../cpp/anonymous-class-types.md)  
  
-   [Punteros a miembros](../cpp/pointers-to-members.md)  
  
-   [this \(Puntero\)](../cpp/this-pointer.md)  
  
-   [Campos de bits de C\+\+](../cpp/cpp-bit-fields.md)  
  
 Los tres tipos de clase son estructura, clase, y unión.  Se declaran mediante las palabras clave [struct](../cpp/struct-cpp.md), [class](../cpp/class-cpp.md) y [union](../cpp/unions.md) \(vea [Definir tipos de clase](http://msdn.microsoft.com/es-es/e8c65425-0f3a-4dca-afc2-418c3b1e57da)\).  En la tabla siguiente se muestran las diferencias entre los tres tipos de clase.  
  
 Para obtener más información sobre las uniones, vea [Unions](../cpp/unions.md).  Para obtener información sobre las clases administradas y los structs, vea [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### Control de acceso y restricciones de las estructuras, clases y uniones  
  
|Estructuras|Clases|Uniones|  
|-----------------|------------|-------------|  
|La clave de clase es `struct`|La clave de clase es **class**|La clave de clase es **union**|  
|El acceso predeterminado es público|El acceso predeterminado es privado|El acceso predeterminado es público|  
|No hay ninguna restricción de uso|No hay ninguna restricción de uso|Usan solo un miembro cada vez|  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)