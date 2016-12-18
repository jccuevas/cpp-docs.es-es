---
title: "vector&lt;bool&gt; (Clase) | Microsoft Docs"
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
  - "vector<bool>"
  - "std.vector<bool>"
  - "std::vector<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector < bool > (clase)"
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vector&lt;bool&gt; (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La `vector<bool>` clase es una especialización parcial de [vector](vector%20Class.md) para elementos de tipo `bool`. Tiene un asignador para el tipo subyacente que utiliza la especialización, que proporciona optimización de espacio porque almacena un valor `bool` por bit.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Allocator = allocator<bool>>  
class vector<bool, Allocator>  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta especialización de plantilla de clase se comporta como vector, salvo por las diferencias que se explican en este artículo.  
  
 Las operaciones que se ocupan del tipo `bool` corresponden a los valores del almacén del contenedor. `allocator_traits::construct` no se utiliza para construir estos valores.  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[const_pointer](#vector_lt_bool_gt___const_pointer)|Una definición de tipo a un `const_iterator` que puede servir como puntero constante para un elemento booleano de `vector<bool>`.|  
|[const_reference](#vector_lt_bool_gt___const_reference)|Una definición de tipo para `bool`. Después de la inicialización, no respeta actualizaciones al valor original.|  
|[puntero](#vector_lt_bool_gt___pointer)|Una definición de tipo para `iterator` que puede servir como puntero a un elemento booleano de `vector<bool>`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[Voltear](#vector_lt_bool_gt___flip)|Invierte todos los bits de `vector<bool>`.|  
|[intercambio](#vector_lt_bool_gt___swap)|Intercambia los elementos de dos `vector<bool>`.|  
|[operador &#91; &#93;](#vector_lt_bool_gt___operator_at)|Devuelve una referencia simulada al elemento `vector<bool>` en una posición especificada.|  
|`at`|Funciona igual que el no especializada [vector](vector%20Class.md):: en función, salvo que use la clase de proxy [vector \< bool>:: referencia](#vector_lt_bool_gt___reference_class). Consulte también [operador &#91; &#93;](#vector_lt_bool_gt___operator_at).|  
|`front`|Funciona igual que el no especializada [vector](vector%20Class.md):: front (función), salvo que usa la clase de proxy [vector \< bool>:: referencia](#vector_lt_bool_gt___reference_class). Consulte también [operador &#91; &#93;](#vector_lt_bool_gt___operator_at).|  
|`back`|Funciona igual que el no especializada [vector](vector%20Class.md):: hacer copia de función, salvo que usa la clase de proxy [vector \< bool>:: referencia](#vector_lt_bool_gt___reference_class). Consulte también [operador &#91; &#93;](#vector_lt_bool_gt___operator_at).|  
  
### <a name="proxy-class"></a>Clase proxy  
  
|||  
|-|-|  
|[vector \< bool> hacen referencia a clase](#vector_lt_bool_gt___reference_class)|Una clase que actúa como proxy para simular el comportamiento de `bool&` y cuyos objetos pueden proporcionar referencias a elementos (bits únicos) dentro de un objeto `vector<bool>`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \< vector>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namevectorltboolgtconstpointera-vectorboolconstpointer"></a><a name="vector_lt_bool_gt___const_pointer"></a>  vector \< bool>:: const_pointer  
 Tipo que describe un objeto que puede actuar como puntero constante a un elemento booleano de la secuencia que contiene el objeto `vector<bool>`.  
  
```  
typedef const_iterator const_pointer;  
```  
  
##  <a name="a-namevectorltboolgtconstreferencea-vectorboolconstreference"></a><a name="vector_lt_bool_gt___const_reference"></a>  vector \< bool>:: const_reference  
 Tipo que describe un objeto que puede actuar como referencia constante a un elemento booleano de la secuencia que contiene el objeto `vector<bool>`.  
  
```  
typedef bool const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información y ejemplos de código, consulte [vector&lt;bool&gt;:: operator =](#vector_lt_bool_gt___reference_operator_eq).  
  
##  <a name="a-namevectorltboolgtflipa-vectorboolflip"></a><a name="vector_lt_bool_gt___flip"></a>  vector \< bool>:: voltear  
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
  
##  <a name="a-namevectorltboolgtoperatorata-vectorbooloperator"></a><a name="vector_lt_bool_gt___operator_at"></a>  vector \< bool>:: operator]  
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
 Un [vector \< bool>:: referencia](#vector_lt_bool_gt___reference_class) o [vector \< bool>:: const_reference](#vector_lt_bool_gt___const_reference) objeto que contiene el valor del elemento indizado.  
  
 Si la posición especificada es mayor o igual que el tamaño del contenedor, el resultado es sin definir.  
  
### <a name="remarks"></a>Comentarios  
 Si compila con `_ITERATOR_DEBUG_LEVEL`, se genera un error en tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites del vector.  Para obtener más información, consulta [Checked Iterators](../standard-library/checked-iterators.md).  
  
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
  
    //    bool* pb = &vb[1]; // conversion error -                         do not use  
    //    bool& refb = vb[1];   // conversion error -                         do not use  
    bool hold = vb[1];  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
  
    // Note this doesn't modify hold.  
    vb[1] = true;  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
}  
  
```  
  
##  <a name="a-namevectorltboolgtpointera-vectorboolpointer"></a><a name="vector_lt_bool_gt___pointer"></a>  vector \< bool>:: puntero  
 Un tipo que describe un objeto que puede actuar como puntero a un elemento booleano de la secuencia contenida en el objeto `vector<bool>`.  
  
```  
typedef iterator pointer;  
```  
  
##  <a name="a-namevectorltboolgtreferenceclassa-vectorboolreference-class"></a><a name="vector_lt_bool_gt___reference_class"></a>  vector \< bool>:: hacen referencia a clase  
 El `vector<bool>::reference` es una clase proxy proporcionada por el [vector \< bool> clase](../standard-library/vector-bool-class.md) para simular `bool&`.  
  
### <a name="remarks"></a>Comentarios  
 Se requiere una referencia simulada porque C++ no permite de forma nativa referencias directas a bits. `vector<bool>` solo utiliza un bit por elemento, al que se puede hacer referencia mediante esta clase proxy. Sin embargo, la simulación de referencia no se completa porque algunas asignaciones no son válidas. Por ejemplo, porque la dirección de la `vector<bool>::reference` objeto no se puede realizar, el siguiente código que usa [vector \< bool>:: operator &#91; &#93;](#vector_lt_bool_gt___operator_at) no es correcta:  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error -         do not use  
    bool& refb = vb[1];   // conversion error -         do not use  
```  
  
###  <a name="a-namevectorltboolgtreferenceflipa-vectorboolreferenceflip"></a><a name="vector_lt_bool_gt___reference_flip"></a>  vector \< bool>:: Reference:: Flip  
 Invierte el valor booleano de una referencia [vector \< bool>](../standard-library/vector-bool-class.md) elemento.  
  
```  
void flip();
```  
  
#### <a name="remarks"></a>Comentarios  
  
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
/* Output:  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
    */  
  
```  
  
###  <a name="a-namevectorltboolgtreferenceoperatorboola-vectorboolreferenceoperator-bool"></a><a name="vector_lt_bool_gt___reference_operator_bool"></a>  vector \< bool>:: operator bool  
 Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.  
  
''' operador bool() const;
```  
  
#### Return Value  
 The Boolean value of the element of the vector<bool\> object.  
  
#### Remarks  
 The `vector<bool>` object cannot be modified by this operator.  
  
###  <a name="vector_lt_bool_gt___reference_operator_eq"></a>  vector<bool\>::reference::operator=  
 Assigns a Boolean value to a bit, or the value held by a referenced element to a bit.  
  
```  
operador de referencia & = (referencia const & derecha);

operador de referencia & =(bool Val);
```  
  
#### Parameters  
 `Right`  
 The element reference whose value is to be assigned to the bit.  
  
 `Val`  
 The Boolean value to be assigned to the bit.  
  
#### Example  
  
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
/* Output:  
The vector is: true false false true true  
The original value of the 1st element stored in a bool: true  
The original value of the 2nd element stored in a bool: false  
The original value of the 3rd element stored in a bool: false  
  
The vector after assigning refelem1 to refelem2 is now: true true false true true  
The vector after assigning false to refelem1 is now: true true true true true  
The original value of the 1st element still stored in a bool: true  
The original value of the 2nd element still stored in a bool: false  
The original value of the 3rd element still stored in a bool: false  
*/  
  
```  
  
##  <a name="a-namevectorltboolgtswapa-vectorboolswap"></a><a name="vector_lt_bool_gt___swap"></a>  vector \< bool>:: swap  
 Función miembro estática que intercambia dos elementos de vectores booleanos ( `vector<bool>`) mediante el uso de la clase de proxy [vector \< bool>:: referencia](#vector_lt_bool_gt___reference_class).  
  
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
 Esta sobrecarga admite los requisitos de proxy especial de `vector<bool>`. [vector](vector%20Class.md):: swap tiene la misma funcionalidad que la sobrecarga de argumento único de `vector<bool>::swap()`.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

