---
title: Clase is_pod | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: efe54ef10c8ab8102e17efdbf8e38f217ec2e0df
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="ispod-class"></a>is_pod (Clase)
Comprueba si el tipo es POD.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct is_pod;
```  
  
#### <a name="parameters"></a>Parámetros  
*T*  
Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
`is_pod<T>::value` es `true` si el tipo *T* es de datos antiguos sin formato (POD). De lo contrario, es `false`.  
  
Los tipos aritméticos, tipos de enumeración, tipos de puntero y el puntero a tipos de miembro son POD.  
  
Una versión cv completa de un tipo POD es en sí misma un tipo POD.  
  
Una matriz de POD es en sí misma POD.  
  
Una estructura o unión cuyos miembros de datos no estáticos son todos POD, es en sí misma POD si reúne estas condiciones:  
  
-   No hay ningún constructor declarado por el usuario.  
  
-   No hay ningún miembro de datos no estáticos privado o protegido.  
  
-   Ninguna clase base.  
  
-   No hay funciones virtuales.  
  
-   No hay ningún miembro de datos no estáticos de tipo de referencia.  
  
-   No hay ningún operador de asignación de copia definido por el usuario.  
  
-   No hay ningún destructor definido por el usuario.  
  
Por lo tanto, puede compilar recursivamente estructuras y matrices POD que contienen estructuras y matrices POD.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial {   
    int val;   
};   
  
struct throws {   
    throws() {}  // User-declared ctor, so not POD
  
    int val;   
};   
  
int main() {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
is_pod<trivial> == true  
is_pod<int> == true  
is_pod<throws> == false  
```  
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** \<type_traits>  
  
**Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[<type_traits>](../standard-library/type-traits.md)




