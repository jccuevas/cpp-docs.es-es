---
title: "&lt; vector &gt; | Microsoft Docs"
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
  - "<vector>"
  - "std.<vector>"
  - "std::<vector>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector (encabezado)"
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; vector &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define el vector de clases de plantilla de contenedores y varias plantillas auxiliares.  
  
 El `vector` es un contenedor que organiza los elementos de un tipo determinado en una secuencia lineal. Permite el acceso aleatorio rápido a cualquier elemento, así como agregar y eliminar elementos de la secuencia de forma dinámica. El `vector` es el contenedor más apropiado para una secuencia cuando el rendimiento de acceso aleatorio es importante.  
  
 Para obtener más información acerca de la clase `vector`, consulte [vector, clase](vector%20Class.md). Para obtener información sobre la especialización `vector<bool>`, consulte [vector \< bool> clase](../standard-library/vector-bool-class.md).  
  
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
  
 ` left`  
 Primer vector (izquierdo) en una operación de comparación  
  
 ` right`  
 Segundo vector (derecho) en una operación de comparación.  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[¡operador! =](../Topic/%3Cvector%3E%20operators.md#operator_neq)|Comprueba si el objeto de vector en el lado izquierdo del operador no es igual que el objeto de vector en el lado derecho.|  
|[operador <](../Topic/%3Cvector%3E%20operators.md#operator_lt_)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor que el objeto de vector en el lado derecho.|  
|[operador \< =](../Topic/%3Cvector%3E%20operators.md#operator_lt__eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor o igual que el objeto de vector en el lado derecho.|  
|[operador ==](../Topic/%3Cvector%3E%20operators.md#operator_eq_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es igual que el objeto de vector en el lado derecho.|  
|[operador >](../Topic/%3Cvector%3E%20operators.md#operator_gt_)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor que el objeto de vector en el lado derecho|  
|[operador > =](../Topic/%3Cvector%3E%20operators.md#operator_gt__eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor o igual que el objeto de vector en el lado derecho|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[vector (clase)](vector%20Class.md)|Una clase de plantilla de contenedores de secuencias que organiza los elementos de un tipo determinado en una organización lineal y permite el acceso aleatorio rápido a cualquier elemento.|  
  
### <a name="specializations"></a>Especializaciones  
  
|||  
|-|-|  
|[vector \< bool> (clase)](../standard-library/vector-bool-class.md)|Una especialización completa de la clase de plantilla vector para los elementos del tipo `bool` con un asignador para el tipo subyacente utilizado por la especialización.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< vector>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

