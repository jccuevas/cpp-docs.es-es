---
title: vector&lt;bool&gt; (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> class
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
caps.latest.revision: 29
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
ms.openlocfilehash: 535ce75fb600b919b5e255bc580a93e448e81d59
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt; (Clase)
La clase `vector<bool>` es una especialización parcial de [vector](../standard-library/vector-class.md) para los elementos de tipo `bool`. Tiene un asignador para el tipo subyacente que utiliza la especialización, que proporciona optimización de espacio porque almacena un valor `bool` por bit.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Allocator = allocator<bool>>  
class vector<bool, Allocator>  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta especialización de la plantilla de clase se comporta como vector, salvo por las diferencias que se explican en este artículo.  
  
 Las operaciones que se ocupan del tipo `bool` corresponden a los valores del almacén del contenedor. `allocator_traits::construct` no se utiliza para construir estos valores.  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[const_pointer](#const_pointer)|Una definición de tipo a un `const_iterator` que puede servir como puntero constante para un elemento booleano de `vector<bool>`.|  
|[const_reference](#const_reference)|Una definición de tipo para `bool`. Después de la inicialización, no respeta actualizaciones al valor original.|  
|[pointer](#pointer)|Una definición de tipo para `iterator` que puede servir como puntero a un elemento booleano de `vector<bool>`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[flip](#flip)|Invierte todos los bits de `vector<bool>`.|  
|[swap](#swap)|Intercambia los elementos de dos `vector<bool>`.|  
|[operator&#91;&#93;](#op_at)|Devuelve una referencia simulada al elemento `vector<bool>` en una posición especificada.|  
|`at`|Funciona igual que la función no especializada [vector](../standard-library/vector-class.md)::at, pero usa la clase de proxy [vector\<bool>::reference](#reference_class). Vea también [operator&#91;&#93;](#op_at).|  
|`front`|Funciona igual que la función no especializada [vector](../standard-library/vector-class.md)::front, pero usa la clase de proxy [vector\<bool>::reference](#reference_class). Vea también [operator&#91;&#93;](#op_at).|  
|`back`|Funciona igual que la función no especializada [vector](../standard-library/vector-class.md)::back, pero usa la clase de proxy [vector\<bool>::reference](#reference_class). Vea también [operator&#91;&#93;](#op_at).|  
  
### <a name="proxy-class"></a>Clase proxy  
  
|||  
|-|-|  
|[Clase de referencia vector\<bool>](#reference_class)|Una clase que actúa como proxy para simular el comportamiento de `bool&` y cuyos objetos pueden proporcionar referencias a elementos (bits únicos) dentro de un objeto `vector<bool>`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \<vector>  
  
 **Espacio de nombres:** std  
  
##  <a name="const_pointer"></a>  vector\<bool>::const_pointer  
 Tipo que describe un objeto que puede actuar como puntero constante a un elemento booleano de la secuencia que contiene el objeto `vector<bool>`.  
  
```  
typedef const_iterator const_pointer;  
```  
  
##  <a name="const_reference"></a>  vector\<bool>::const_reference  
 Tipo que describe un objeto que puede actuar como referencia constante a un elemento booleano de la secuencia que contiene el objeto `vector<bool>`.  
  
```  
typedef bool const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para más información y ejemplos de código, vea [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq).  
  
##  <a name="flip"></a>  vector\<bool>::flip  
 Invierte todos los bits de `vector<bool>`.  
  
```  
void flip();
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_bool_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha; // format output for subsequent code  
  
    vector<bool> vb = { true, false, false, true, true };  
    cout << "The vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vb.flip();  
  
    cout << "The flipped vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="op_at"></a>  vector\<bool>::operator[]  
 Devuelve una referencia simulada al elemento `vector<bool>` en una posición especificada.  
  
```  
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Pos`|Posición del elemento `vector<bool>`.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto [vector\<bool>::reference](#reference_class) o [vector\<bool>::const_reference](#const_reference) que contiene el valor del elemento indizado.  
  
 Si la posición especificada es mayor o igual que el tamaño del contenedor, el resultado es sin definir.  
  
### <a name="remarks"></a>Comentarios  
 Si compila con `_ITERATOR_DEBUG_LEVEL`, se genera un error en tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites del vector.  Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  En este ejemplo de código se muestra el uso correcto de `vector<bool>::operator[]` y dos errores habituales de codificación, que están comentados. Estos errores se producen porque no se puede tomar la dirección del objeto `vector<bool>::reference` que devuelve `vector<bool>::operator[]`.  
  
```cpp  
// cl.exe /EHsc /nologo /W4 /MTd   
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
    vector<bool> vb;  
  
    vb.push_back(true);  
    vb.push_back(false);  
  
    //    bool* pb = &vb[1]; // conversion error - do not use  
    //    bool& refb = vb[1];   // conversion error - do not use  
    bool hold = vb[1];  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
  
    // Note this doesn't modify hold.  
    vb[1] = true;  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
}  
```  
  
##  <a name="pointer"></a>  vector\<bool>::pointer  
 Un tipo que describe un objeto que puede actuar como puntero a un elemento booleano de la secuencia contenida en el objeto `vector<bool>`.  
  
```  
typedef iterator pointer;  
```  
  
##  <a name="reference_class"></a>  vector\<bool>::reference Class  
 La clase `vector<bool>::reference` es una clase de proxy proporcionada por [vector\<bool> (Clase)](../standard-library/vector-bool-class.md) para simular `bool&`.  
  
### <a name="remarks"></a>Comentarios  
 Se requiere una referencia simulada porque C++ no permite de forma nativa referencias directas a bits. `vector<bool>` solo utiliza un bit por elemento, al que se puede hacer referencia mediante esta clase proxy. Sin embargo, la simulación de referencia no se completa porque algunas asignaciones no son válidas. Por ejemplo, dado que no se puede tomar la dirección del objeto `vector<bool>::reference`, el siguiente código, que usa [vector\<bool>::operator&#91;&#93;](#op_at), no es correcto:  
  
```cpp  
vector<bool> vb;  
//...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
###  <a name="reference_flip"></a>  vector\<bool>::reference::flip  
 Invierte el valor booleano de un elemento de referencia [vector\<bool>](../standard-library/vector-bool-class.md).  
  
```  
void flip();
```  
  
#### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
```  
  
```Output  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
```  
  
###  <a name="reference_operator_bool"></a>  vector\<bool>::reference::operator bool  
 Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.  
  
```  
operator bool() const;
```  
  
#### <a name="return-value"></a>Valor devuelto  
 El valor booleano del elemento del objeto vector\<bool>.  
  
#### <a name="remarks"></a>Comentarios  
 Este operador no puede modificar el objeto `vector<bool>`.  
  
###  <a name="reference_operator_eq"></a>  vector\<bool>::reference::operator=  
 Asigna un valor booleano a un bit o asigna el valor contenido en un elemento al que se hace referencia a un bit.  
  
```  
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```  
  
#### <a name="parameters"></a>Parámetros  
 `Right`  
 Referencia del elemento cuyo valor se asigna al bit.  
  
 `Val`  
 Valor booleano que se asigna al bit.  
  
#### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_bool_ref_op_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    print("The vector is: ", vb);  
  
    // Invoke vector<bool>::reference::operator=()  
    vector<bool>::reference refelem1 = vb[0];  
    vector<bool>::reference refelem2 = vb[1];  
    vector<bool>::reference refelem3 = vb[2];  
  
    bool b1 = refelem1;  
    bool b2 = refelem2;  
    bool b3 = refelem3;  
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;  
    cout << endl;  
  
    refelem2 = refelem1;  
  
    print("The vector after assigning refelem1 to refelem2 is now: ", vb);  
  
    refelem3 = true;  
  
    print("The vector after assigning false to refelem1 is now: ", vb);  
  
    // The initial values are still stored in the bool variables and remained unchanged  
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;  
    cout << endl;  
}  
```  
  
```Output  
The vector is: true false false true true  
The original value of the 1st element stored in a bool: true  
The original value of the 2nd element stored in a bool: false  
The original value of the 3rd element stored in a bool: false  
  
The vector after assigning refelem1 to refelem2 is now: true true false true true  
The vector after assigning false to refelem1 is now: true true true true true  
The original value of the 1st element still stored in a bool: true  
The original value of the 2nd element still stored in a bool: false  
The original value of the 3rd element still stored in a bool: false  
```  
  
##  <a name="swap"></a>  vector\<bool>::swap  
 Función miembro estática que intercambia dos elementos de vectores booleanos ( `vector<bool>`) mediante la clase de proxy [vector\<bool>::reference](#reference_class).  
  
```  
static void swap(
    reference Left,  
    reference Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Elemento que se va a intercambiar con el elemento `Right`.  
  
 `Right`  
 Elemento que se va a intercambiar con el elemento `Left`.  
  
### <a name="remarks"></a>Comentarios  
 Esta sobrecarga admite los requisitos de proxy especial de `vector<bool>`. [vector](../standard-library/vector-class.md)::swap tiene la misma funcionalidad que la sobrecarga de un solo argumento de `vector<bool>::swap()`.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


