---
title: type_info (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_info
dev_langs:
- C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b87dec1f3d3a04d984c3bbd96344ebcb0a163f19
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="typeinfo-class"></a>type_info (Clase)
El **type_info** clase describe información de tipo generada en el programa por el compilador. Los objetos de esta clase almacenan de forma eficaz un puntero a un nombre para el tipo. El **type_info** clase también almacena un valor codificado adecuado para comparar dos tipos de igualdad u orden de intercalación. Las reglas de codificación y la secuencia de intercalación para tipos no se especifican y pueden diferir entre programas.  
  
 El `<typeinfo>` archivo de encabezado se debe incluir para poder usar el **type_info** clase. La interfaz para la **type_info** clase es:  
  
```cpp
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 No se puede crear instancias de objetos de la **type_info** clase directamente, porque la clase tiene un constructor de copias privado. La única manera de construir (temporal) **type_info** objeto consiste en utilizar el [typeid](../cpp/typeid-operator.md) operador. Puesto que el operador de asignación también es privado, no puede copiar ni asignar objetos de clase **type_info**.  
  
 **type_info:: hash_code** define una función hash adecuada para la asignación de valores de tipo **typeinfo** a una distribución de valores de índice.  
  
 Los operadores `==` y `!=` puede utilizarse para comparar la igualdad y desigualdad con otros **type_info** objetos, respectivamente.  
  
 No hay ningún vínculo entre el orden de intercalación de tipos y las relaciones de herencia. Use la **type_info:: before** para determinar la secuencia de intercalación de tipos de función miembro. No hay ninguna garantía de que **type_info:: before** producirá el mismo resultado en programas diferentes o incluso ejecuciones diferentes del mismo programa. De esta manera, **type_info:: before** es similar a la dirección del **(&)** operador.  
  
 El **type_info:: Name** función miembro devuelve un **const char\* ** a una cadena terminada en null que representa el nombre legible del tipo. La memoria a la que se señala se almacena en caché y nunca debe desasignarse directamente.  
  
 El **type_info:: raw_name** función miembro devuelve un **const char\* ** a una cadena terminada en null que representa el nombre representativo del tipo de objeto. El nombre se almacena realmente en forma representativa para ahorrar espacio. Por lo tanto, esta función es más rápida que **type_info:: Name** porque no es necesario quitar la decoración de nombre. La cadena devuelta por la **type_info:: raw_name** función es útil en operaciones de comparación, pero no es legible. Si necesita una cadena legible para el usuario, use la **type_info:: Name** funcione en su lugar.  
  
 Información de tipo se genera para solo si de las clases polimórficas el [/GR (habilitar información de tipo en tiempo de ejecución)](../build/reference/gr-enable-run-time-type-information.md) se especifica la opción del compilador.  
  
## <a name="see-also"></a>Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)

