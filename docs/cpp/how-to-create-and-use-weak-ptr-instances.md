---
title: "C&#243;mo: Crear y usar instancias de weak_ptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Crear y usar instancias de weak_ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto debe almacenar a veces una manera de tener acceso al objeto subyacente de `shared_ptr` sin que el recuento de referencias se incremente.  Normalmente, esta situación se produce cuando hay referencias cíclicas entre instancias `shared_ptr`.  
  
 El mejor diseño es evitar la propiedad compartida de punteros siempre que pueda.  Sin embargo, si debe haber compartido la propiedad de las instancias de `shared_ptr`, evite las referencias cíclicas entre ellas.  Cuando son cíclicas las referencias son inevitables, o incluso preferibles por alguna razón, utilice `weak_ptr` para dar a uno o más de los propietarios una referencia parcial a otro `shared_ptr`.  Mediante `weak_ptr`, puede crear `shared_ptr` que combina un conjunto existente de instancias relacionadas, pero solo si el recurso de memoria subyacente todavía es válido.  `weak_ptr` no participa por si mismo en el recuento de referencias y, por consiguiente, no puede impedir que el recuento de referencias vaya hacia cero.  Sin embargo, puede utilizar `weak_ptr` para intentar obtener una nueva copia de `shared_ptr` con la que se inicializó.  Si la memoria ya se ha eliminado, se produce una excepción de **bad\_weak\_ptr**.  Si la memoria es aún válida, el nuevo puntero compartido incrementa el recuento de referencias y garantiza que la memoria será válida mientras la variable de `shared_ptr` permanezca dentro del ámbito.  
  
## Ejemplo  
 El ejemplo de código siguiente muestra un caso donde `weak_ptr` se utiliza para garantizar la eliminación correcta de los objetos que tienen dependencias circulares.  Mientras examina el ejemplo, suponga que solo se creó después de considerar las soluciones.  Los objetos de `Controller` representan algún aspecto de un proceso de equipo y funcionan independientemente.  Cada controlador debe poder consultar el estado de los demás controladores en cualquier momento, y cada uno contiene un `vector<weak_ptr<Controller>>` privado para este fin.  Cada vector contiene una referencia circular y, por consiguiente, las instancias de `weak_ptr` se utilizan en lugar de las de `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
  **Crear controlador0**  
**Crear controlador1**  
**Crear controlador2**  
**Crear controlador3**  
**Crear controlador4**  
**push\_back to v\[0\]: 1**  
**push\_back to v\[0\]: 2**  
**push\_back to v\[0\]: 3**  
**push\_back to v\[0\]: 4**  
**push\_back to v\[1\]: 0**  
**push\_back to v\[1\]: 2**  
**push\_back to v\[1\]: 3**  
**push\_back to v\[1\]: 4**  
**push\_back to v\[2\]: 0**  
**push\_back to v\[2\]: 1**  
**push\_back to v\[2\]: 3**  
**push\_back to v\[2\]: 4**  
**push\_back to v\[3\]: 0**  
**push\_back to v\[3\]: 1**  
**push\_back to v\[3\]: 2**  
**push\_back to v\[3\]: 4**  
**push\_back to v\[4\]: 0**  
**push\_back to v\[4\]: 1**  
**push\_back to v\[4\]: 2**  
**push\_back to v\[4\]: 3**  
**use\_count \= 1**  
**Status of 1 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**Status of 1 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**Status of 1 \= On**  
**Status of 2 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**Status of 1 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Destruir controller0**  
**Destruir controller1**  
**Destruir controller2**  
**Destruir controller3**  
**Destruir controller4**  
**Presione cualquier tecla** Como experimento, modifique el vector `others` para que sea un `vector<shared_ptr<Controller>>`y, en la salida, observe que no se invoca ningún destructor cuando `TestRun` devuelve.  
  
## Vea también  
 [Punteros inteligentes](../cpp/smart-pointers-modern-cpp.md)