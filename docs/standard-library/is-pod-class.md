---
title: Clase is_pod | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_pod
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
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 2236d6a9796b1353b919a63620606242cde169bd
ms.lasthandoff: 02/24/2017

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




