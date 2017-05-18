---
title: '&lt;vector&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <vector>
- std.<vector>
- std::<vector>
dev_langs:
- C++
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 77c13a5f8d813bbeaa0dae2307769a575bb22fa8
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltvectorgt"></a>&lt;vector&gt;
Define el vector de clases de plantilla de contenedores y varias plantillas auxiliares.  
  
 El `vector` es un contenedor que organiza los elementos de un tipo determinado en una secuencia lineal. Permite el acceso aleatorio rápido a cualquier elemento, así como agregar y eliminar elementos de la secuencia de forma dinámica. El `vector` es el contenedor más apropiado para una secuencia cuando el rendimiento de acceso aleatorio es importante.  
  
 Para más información sobre la clase `vector`, vea [vector (Clase)](../standard-library/vector-class.md). Para más información sobre la especialización `vector<bool>`, vea [vector\<bool> (Clase)](../standard-library/vector-bool-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace std {  
template <class Type, class Allocator>  
class vector;  
template <class Allocator>  
class vector<bool>;  
 
template <class Allocator>  
struct hash<vector<bool, Allocator>>;  
 // TEMPLATE FUNCTIONS  
template <class Type, class Allocator>  
bool operator== (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator!= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<(
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator> (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator>= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
void swap (
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);

}  // namespace std  
```  
  
#### <a name="parameters"></a>Parámetros  
 Tipo  
 Parámetro de plantilla para el tipo de datos almacenados en el vector.  
  
 Asignador  
 Parámetro de plantilla para el objeto de asignador almacenado responsable de la asignación y desasignación de memoria.  
  
 `left`  
 Primer vector (izquierdo) en una operación de comparación  
  
 `right`  
 Segundo vector (derecho) en una operación de comparación.  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator! =](../standard-library/vector-operators.md#op_neq)|Comprueba si el objeto de vector en el lado izquierdo del operador no es igual que el objeto de vector en el lado derecho.|  
|[operator<](../standard-library/vector-operators.md#op_lt)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor que el objeto de vector en el lado derecho.|  
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor o igual que el objeto de vector en el lado derecho.|  
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es igual que el objeto de vector en el lado derecho.|  
|[operator>](../standard-library/vector-operators.md#op_gt)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor que el objeto de vector en el lado derecho|  
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor o igual que el objeto de vector en el lado derecho|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[vector (Clase)](../standard-library/vector-class.md)|Una clase de plantilla de contenedores de secuencias que organiza los elementos de un tipo determinado en una organización lineal y permite el acceso aleatorio rápido a cualquier elemento.|  
  
### <a name="specializations"></a>Especializaciones  
  
|||  
|-|-|  
|[vector\<bool> (Clase)](../standard-library/vector-bool-class.md)|Una especialización completa de la clase de plantilla vector para los elementos del tipo `bool` con un asignador para el tipo subyacente utilizado por la especialización.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<vector>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


