---
title: "enable_shared_from_this (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1.enable_shared_from_this"
  - "enable_shared_from_this"
  - "std.tr1.enable_shared_from_this"
  - "memory/std::tr1::enable_shared_from_this"
  - "std::tr1::enable_shared_from_this"
  - "tr1::enable_shared_from_this"
  - "std.enable_shared_from_this"
  - "memory/std::enable_shared_from_this"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enable_shared_from_this (clase)"
  - "enable_shared_from_this (clase) [TR1]"
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# enable_shared_from_this (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ayuda a generar un `shared_ptr`.  
  
## Sintaxis  
  
```  
template<class Ty>  
    class enable_shared_from_this {  
public:  
    shared_ptr<Ty> shared_from_this();  
    shared_ptr<const Ty> shared_from_this() const;  
  
protected:  
    enable_shared_from_this();  
    enable_shared_from_this(const enable_shared_from_this&);  
    enable_shared_from_this& operator=(const enable_shared_from_this&);  
    ~enable_shared_from_this();  
    };  
```  
  
#### Parámetros  
 `Ty`  
 Tipo controlado por el puntero compartido.  
  
## Comentarios  
 Objetos derivados de `enable_shared_from_this` puede utilizar el `shared_from_this` métodos en las funciones miembro para crear [shared\_ptr](../standard-library/shared-ptr-class.md) los propietarios de la instancia que comparten la propiedad existente `shared_ptr` propietarios. En caso contrario, si crea un nuevo `shared_ptr` utilizando `this`, es distinta de la existente `shared_ptr` propietarios, lo que pueden provocar un no válido de referencias o el objeto se puede eliminar más de una vez.  
  
 Los constructores, el destructor y el operador de asignación están protegidos para evitar el mal uso accidental. El tipo de argumento de plantilla `Ty` debe ser del tipo de la clase derivada.  
  
 Para obtener un ejemplo de uso, consulte [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md).  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md)   
 [shared\_ptr \(Clase\)](../standard-library/shared-ptr-class.md)