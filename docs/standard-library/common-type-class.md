---
title: common_type (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::common_type
dev_langs:
- C++
helpviewer_keywords:
- common_type class
- common_type
ms.assetid: 02bc4e7b-c63d-49de-9f8a-511d3a5c1e7f
caps.latest.revision: 22
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 90b6f671e33af5ae3a58d51d7cbf23f1beed494c
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="commontype-class"></a>common_type (Clase)
Determina el tipo común de uno o más tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class... T>  
struct common_type;

template <class T>  
struct common_type<T> {
    typedef typename decay<T>::type type;
};

template <class T, class U>  
struct common_type<T, U> {
    typedef typename decay<decltype(true declval<T>() :
    declval<U>())>::type type;
};

template <class T, class U, class... V>  
struct common_type<T, U, V...> {
    typedef typename common_type<typename common_type<T, U>::type, V...>::type type;
};
```  
  
#### <a name="parameters"></a>Parámetros  
 Lista de tipos que son [tipos completos](../c-language/incomplete-types.md) o nulos.  
  
## <a name="remarks"></a>Comentarios  
 El miembro `type` es el tipo común al que se pueden convertir todos los tipos de la lista de parámetros.  
  
## <a name="example"></a>Ejemplo  
 El programa siguiente muestra algunos escenarios de uso correctos y realiza pruebas para obtener resultados.  
  
```cpp  
// Compile using cl.exe /EHsc  
// common_type sample  
#include <iostream>  
#include <type_traits>  
  
struct Base {};  
struct Derived : Base {};  
  
int main()   
{  
    typedef std::common_type<unsigned char, short, int>::type NumericType;  
    typedef std::common_type<float, double>::type FloatType;  
    typedef std::common_type<const int, volatile int>::type ModifiedIntType;  
    typedef std::common_type<Base, Derived>::type ClassType;  
  
    std::cout << std::boolalpha;  
    std::cout << "Test for typedefs of common_type int" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<int, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<int, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<int, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<int, ClassType>::value << std::endl;  
    std::cout << "---------------------------" << std::endl;  
    std::cout << "Test for typedefs of common_type double" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<double, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<double, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<double, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<double, ClassType>::value << std::endl;  
    std::cout << "---------------------------" << std::endl;  
    std::cout << "Test for typedefs of common_type Base" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<Base, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<Base, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<Base, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<Base, ClassType>::value << std::endl;  
  
    return 0;  
}  
```  
  
## <a name="output"></a>Salida  
  
```
Test for typedefs of common_type int
NumericType: true
FloatType: false
ModifiedIntType: true
ClassType: false
---------------------------
Test for typedefs of common_type double
NumericType: false
FloatType: true
ModifiedIntType: false
ClassType: false
---------------------------
Test for typedefs of common_type Base
NumericType: false
FloatType: false
ModifiedIntType: false
ClassType: true
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




