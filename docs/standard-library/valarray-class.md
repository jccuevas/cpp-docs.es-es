---
title: "valarray (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "valarray"
  - "std.valarray"
  - "std::valarray"
  - "valarray/std::valarray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray (clase)"
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# valarray (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de elementos de tipo **tipo** que se almacena como una matriz, diseñado para realizar operaciones matemáticas a alta velocidad y optimizado para el rendimiento de cálculo.  
  
## <a name="remarks"></a>Comentarios  
 La clase es una representación del concepto matemático de un conjunto ordenado de valores y los elementos se numeran secuencialmente a partir de cero. La clase se define como un contenedor casi porque admite algunas, pero no todas, las capacidades que la primera secuenciación de contenedores, como [vector](vector%20Class.md), admitir. Difiere del vector de clase de plantilla en dos aspectos importantes:  
  
-   Define muchas operaciones aritméticas entre los elementos correspondientes de **valarray \< tipo>** objetos del mismo tipo y longitud, como *xarr* = cos ( *yarr*) + sin ( *zarr*).  
  
-   Define una variedad de formas interesantes de subíndice un **valarray \< tipo>** objeto mediante la sobrecarga de [operador &#91; &#93;](#valarray__operator_at).  
  
 Un objeto de clase **tipo**:  
  
-   Tiene un constructor público predeterminado, un destructor, un constructor de copias y un operador de asignación, con un comportamiento convencional.  
  
-   Define, en la medida que sean necesarios, los operadores aritméticos y las funciones matemáticas que se definen para los tipos de punto flotante con un comportamiento convencional.  
  
 En concreto, no pueden existir diferencias sutiles entre la construcción de la copia y la construcción predeterminada seguida por una asignación. Ninguna de las operaciones en objetos de clase **tipo** pueden producir excepciones.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[valarray](#valarray__valarray)|Construye una `valarray` de un tamaño específico o con elementos de un valor determinado, o como una copia de otra `valarray` o un subconjunto de otra `valarray`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[value_type](#valarray__value_type)|Tipo que representa el tipo de elemento almacenado en una `valarray`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[aplicar](#valarray__apply)|Aplica una función especificada a cada elemento de una `valarray`.|  
|[cshift](#valarray__cshift)|Desplaza de forma cíclica todos los elementos de una `valarray` un número especificado de posiciones.|  
|[liberar](#valarray__free)|Libera la memoria usada por la `valarray`.|  
|[max](#valarray__max)|Busca el elemento más grande en una `valarray`.|  
|[min](#valarray__min)|Busca el elemento más pequeño en una `valarray`.|  
|[cambiar el tamaño](#valarray__resize)|Cambia el número de elementos de una `valarray` por un número especificado, agregando o quitando elementos según sea necesario.|  
|[MAYÚS](#valarray__shift)|Desplaza todos los elementos de una `valarray` un número especificado de posiciones.|  
|[tamaño](#valarray__size)|Busca el número de elementos de una `valarray`.|  
|[suma](#valarray__sum)|Determina la suma de todos los elementos de una `valarray` de longitud distinta de cero.|  
|[intercambio](#valarray__swap)||  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[¡operador!](#valarray__operator_not)|Operador unario que obtiene los valores `NOT` lógicos de cada elemento de una `valarray`.|  
|[operator % =](#valarray__operator_mod_eq)|Obtiene el resto de la división de los elementos de una matriz uno a uno por una `valarray` especificada o por un valor del tipo de elemento.|  
|[operador & =](#valarray__operator_amp__eq)|Obtiene el `AND` bit a bit de los elementos de una matriz con los elementos correspondientes de una `valarray` especificada o con un valor del tipo de elemento.|  
|[operador >> =](#valarray__operator_gt__gt__eq)|Desplaza hacia la derecha los bits de cada elemento de un operando `valarray` un número especificado de posiciones o una cantidad de elementos especificada por una segunda `valarray`.|  
|[operador << =](#valarray__operator_lt__lt__eq)|Desplaza hacia la izquierda los bits de cada elemento de un operando `valarray` un número especificado de posiciones o una cantidad de elementos especificada por una segunda `valarray`.|  
|[operador * =](#valarray__operator_star_eq)|Multiplica los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, por un operando `valarray`.|  
|[operator +](#valarray__operator_add)|Operador unario que aplica un signo más a cada elemento de una `valarray`.|  
|[+= (operador)](#valarray__operator_add_eq)|Suma los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, a un operando `valarray`.|  
|[operator-](#valarray__operator-)|Operador unario que aplica un signo menos a cada elemento de una `valarray`.|  
|[operador =](#valarray__operator-_eq)|Resta los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, de un operando `valarray`.|  
|[/ = (operador)](#valarray__operator__eq)|Divide un operando `valarray` elemento a elemento por los elementos de una `valarray` especificada o un valor del tipo de elemento.|  
|[operador =](#valarray__operator_eq)|Asigna los elementos a una `valarray` cuyos valores se especifican directamente o como parte de otra `valarray` o mediante una `slice_array`, `gslice_array`, `mask_array` o `indirect_array`.|  
|[operador &#91; &#93;](#valarray__operator_at)|Devuelve una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.|  
|[operador ^ =](#valarray__operator_xor_eq)|Obtiene el operador o exclusivo elementos lógico ( `XOR`) de una matriz con una valarray especificada o un valor del tipo de elemento.|  
|[operador &#124; =](#valarray__operator_or_eq)|Obtiene el `OR` bit a bit de los elementos de una matriz con los elementos correspondientes de una `valarray` especificada o con un valor del tipo de elemento.|  
|[operador ~](#valarray__operator_dtor)|Operador unario que obtiene los valores `NOT` bit a bit de cada elemento de una `valarray`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< valarray>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namevalarrayapplya-valarrayapply"></a><a name="valarray__apply"></a>  valarray:: Apply  
 Aplica una función especificada a cada elemento de una valarray.  
  
```  
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *_Func(Type)*  
 El objeto de función que se aplicará a cada elemento de la valarray del operando.  
  
 *_Func(const Type&)*  
 El objeto de función para const que se aplicará a cada elemento de la valarray del operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos se han tenido `_Func` element-wise aplicada a los elementos de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un objeto de clase [valarray](../standard-library/valarray-class.md)**\< tipo>**, de longitud [tamaño](#valarray__size), cada uno de cuyos elementos `I` es **func**(( **\*Esto**) [ `I`]).  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_apply.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
using namespace std;  
  
int __cdecl MyApplyFunc( int n )  
{  
   return n*2;  
}  
  
int main( int argc, char* argv[] )  
{  
   valarray<int> vaR(10), vaApplied(10);  
   int i;  
  
   for ( i = 0; i < 10; i += 3 )  
      vaR[i] = i;  
  
   for ( i = 1; i < 10; i += 3 )  
      vaR[i] = 0;  
  
   for ( i = 2; i < 10; i += 3 )  
      vaR[i] = -i;  
  
   cout << "The initial Right valarray is: (";  
   for   ( i=0; i < 10; ++i )  
      cout << " " << vaR[i];  
   cout << " )" << endl;  
  
   vaApplied = vaR.apply( MyApplyFunc );  
  
   cout << "The element-by-element result of "  
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";  
   for ( i = 0; i < 10; ++i )  
      cout << " " << vaApplied[i];  
   cout << " )" << endl;  
}  
\* Output:   
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )  
The element-by-element result of applying MyApplyFunc to vaR is the  
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )  
*\  
```  
  
##  <a name="a-namevalarraycshifta-valarraycshift"></a><a name="valarray__cshift"></a>  valarray:: cshift  
 Desplaza todos los elementos en una valarray cíclicamente un número especificado de posiciones.  
  
```  
valarray<Type> cshift(int count) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 El número de posiciones de los elementos es se desplace hacia adelante.  
  
### <a name="return-value"></a>Valor devuelto  
 Una nueva valarray en la que todos los elementos que se han movido ` count` posiciones cíclica hacia la parte delantera de la valarray, izquierda con respecto a sus posiciones en la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 Un valor positivo de ` count` desplaza los elementos cíclicamente izquierda ` count` coloca.  
  
 Un valor negativo de ` count` desplaza los elementos cíclicamente derecho ` count` coloca.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_cshift.cpp  
// compile with: /EHsc  
  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    valarray<int> va1(10), va2(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
    for (i = 0; i < 10; i+=1)  
        va2[i] = 10 - i;  
  
    cout << "The operand valarray va1 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    // A positive parameter shifts elements right  
    va1 = va1.cshift(4);  
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    cout << "The operand valarray va2 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
  
    // A negative parameter shifts elements left  
    va2 = va2.cshift(-4);  
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
}  
\* Output:   
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)  
The cyclically shifted valarray va1 is:  
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)  
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)  
The cyclically shifted valarray va2 is:  
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)  
*\  
```  
  
##  <a name="a-namevalarrayfreea-valarrayfree"></a><a name="valarray__free"></a>  valarray:: Free  
 Libera la memoria utilizada por la valarray.  
  
```  
void free();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función no estándar es equivalente a asignar valarray vacía. Por ejemplo:  
  
```  
valarray<T> v;  
v = valarray<T>();

// equivalent to v.free()  
```  
  
##  <a name="a-namevalarraymaxa-valarraymax"></a><a name="valarray__max"></a>  valarray:: max  
 Busca el elemento más grande de una valarray.  
  
```  
Type max() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor máximo de los elementos de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro compara valores aplicando **operador \<** o **operador >** entre los pares de elementos de la clase **tipo**, para qué operadores se debe proporcionar para el elemento **tipo**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_max.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MaxValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i - 1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  10 - i;  
  
   cout << "The operand valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MaxValue = vaR.max (  );  
   cout << "The largest element in the valarray is: "  
        << MaxValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).  
The largest element in the valarray is: 13.  
*\  
```  
  
##  <a name="a-namevalarraymina-valarraymin"></a><a name="valarray__min"></a>  valarray:: min  
 Busca el elemento más pequeño de una valarray.  
  
```  
Type min() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor mínimo de los elementos de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro compara valores aplicando **operador \<** o **operador >** entre los pares de elementos de la clase **tipo**, para qué operadores se debe proporcionar para el elemento **tipo**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_min.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MinValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  5 - i;  
  
   cout << "The operand valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MinValue = vaR.min ( );  
   cout << "The smallest element in the valarray is: "  
        << MinValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).  
The smallest element in the valarray is: -9.  
*\  
```  
  
##  <a name="a-namevalarrayoperatornota-valarrayoperator"></a><a name="valarray__operator_not"></a>  ¡valarray:: operator!  
 Un operador unario que obtiene la lógica **NO** valores de cada elemento en una valarray.  
  
```  
valarray<bool> operator!() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valarray de valores booleanos que son la negación de los valores de los elementos de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 La operación lógica **NO** niega los elementos porque y convierte todos los ceros en las que se refiere a todos los valores distintos de cero que las y convierte en ceros. La valarray de valores booleanos devuelta es el mismo tamaño que la valarray del operando.  
  
 También hay un bit a bit **NO**[valarray:: operator ~](#valarray__operator_dtor) que niega el nivel de bits individuales dentro de la representación binaria de `char` y `int` elementos de un valarray.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_lognot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<bool> vaNOT ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT = !vaL;  
   cout << "The element-by-element result of "  
        << "the logical NOT operator! is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The element-by-element result of the logical NOT operator! is the  
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatormodeqa-valarrayoperator"></a><a name="valarray__operator_mod_eq"></a>  valarray:: operator % =  
 Obtiene el resto de dividir los elementos de una matriz de element-wise una valarray especificada o un valor del tipo de elemento.  
  
```  
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valarray o el valor de un tipo de elemento idéntico de la valarray del operando que consiste en dividir, element-wise, la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son el resto de la división de elementos de la valarray operando por ` right.`  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_class_op_rem.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  53;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -67;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  3*i+1;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL %= vaR;  
   cout << "The remainders from the element-by-element "  
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial  right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorampeqa-valarrayoperatoramp"></a><a name="valarray__operator_amp__eq"></a>  valarray:: operator&amp;=  
 Obtiene el bit a bit **AND** de elementos de una matriz con los elementos correspondientes de una valarray especificado o con un valor del tipo de elemento.  
  
```  
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valor de un tipo de elemento idéntico de la valarray del operando que se pueden combinar, elementos por la lógica o valarray **y** con la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son los elementos lógicos **y** de la valarray operando por ` right.`  
  
### <a name="remarks"></a>Comentarios  
 Una operación bit a bit sólo puede utilizarse para manipular los bits de `char` y `int` tipos de datos y sus variantes y no en **float**, **doble**, **longdouble**, `void`, `bool`, u otros, tipos de datos más complejos.  
  
 La operación AND bit a bit tiene la misma tabla de verdad que la lógica **AND** pero que se aplica al tipo de datos en el nivel de los bits individuales. Dados los bits *b*1 y *b*2, *b*1 **AND** *b*2 es **true** Si ambos bits son true; **false** Si al menos uno es false.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_class_op_bitand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL &= vaR;  
   cout << "The element-by-element result of "  
        << "the logical AND operator&= is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&= is the  
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorgtgteqa-valarrayoperatorgtgt"></a><a name="valarray__operator_gt__gt__eq"></a>  valarray:: operator&gt;&gt;=  
 Derecha-desplaza los bits de cada elemento de un operando de valarray un número especificado de posiciones o por una cantidad de elementos especificado por una segundo valarray.  
  
```  
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valor que indica la cantidad de desplazamiento a la derecha o valarray cuyos elementos indican la cantidad de elementos de desplazamiento a la derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos se han sido derecha desplazado a la cantidad especificada en ` right`.  
  
### <a name="remarks"></a>Comentarios  
 Números con signo tienen los signos que se conservan.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_class_op_rs.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  64;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -64;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL >>= vaR;  
   cout << "The element-by-element result of "  
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorltlteqa-valarrayoperatorltlt"></a><a name="valarray__operator_lt__lt__eq"></a>  valarray:: operator&lt;&lt;=  
 Izquierda: desplaza los bits de cada elemento de un operando de valarray un número especificado de posiciones o por una cantidad de elementos especificado por una segundo valarray.  
  
```  
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valor que indica la cantidad de desplazamiento a la izquierda o valarray cuyos elementos indican la cantidad de elementos de desplazamiento a la izquierda.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos se ha desplazado deja la cantidad especificada en ` right`.  
  
### <a name="remarks"></a>Comentarios  
 Números con signo tienen los signos que se conservan.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_class_op_ls.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL <<= vaR;  
   cout << "The element-by-element result of "  
        << "the left shift\n on the operand array is the valarray:\n ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift  
 on the operand array is the valarray:  
 ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorstareqa-valarrayoperator"></a><a name="valarray__operator_star_eq"></a>  valarray:: operator * =  
 Multiplica los elementos de una valarray especificado o un valor del tipo de elemento, element-wise, a una valarray de operando.  
  
```  
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valarray o el valor de un tipo de elemento idéntico de la valarray de operando es multiplicar, element-wise, la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son el producto de elementos de la valarray operando y ` right.`  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_emult.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL *= vaR;  
   cout << "The element-by-element result of "  
        << "the multiplication is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoradda-valarrayoperator"></a><a name="valarray__operator_add"></a>  valarray:: operator +  
 Un operador unario que aplica un signo más para cada elemento en una valarray.  
  
```  
valarray<Type> operator+() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son más aquellos de la matriz de operando.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_eplus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaPLUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaPLUS = +vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaPLUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoraddeqa-valarrayoperator"></a><a name="valarray__operator_add_eq"></a>  valarray:: operator +=  
 Agrega los elementos de una valarray especificado o un valor del tipo de elemento, element-wise, a una valarray de operando.  
  
```  
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valarray o el valor de un tipo de elemento idéntico de la valarray del operando que va a agregarse, element-wise, en la valarray del operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son la suma de elementos de la valarray operando y ` right.`  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_eadd.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL += vaR;  
   cout << "The element-by-element result of "  
        << "the sum is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-a-valarrayoperator-"></a><a name="valarray__operator-"></a>  valarray:: operator-  
 Un operador unario que aplica un signo menos a cada elemento en una valarray.  
  
```  
valarray<Type> operator-() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son menos los de la matriz de operando.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_eminus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaMINUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaMINUS = -vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaMINUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-eqa-valarrayoperator-"></a><a name="valarray__operator-_eq"></a>  valarray:: operator =  
 Resta los elementos de una valarray especificado o un valor del tipo de elemento, element-wise, valarray del operando.  
  
```  
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valarray o el valor de un tipo de elemento idéntico de la valarray del operando que se va a restar, element-wise, de la valarray del operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son la diferencia de elementos de la valarray operando y ` right.`  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_esub.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  10;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL -= vaR;  
   cout << "The element-by-element result of "  
        << "the difference is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator__eq"></a>  valarray:: operator / =  
 Divide el operando valarray element-wise por los elementos de una valarray especificado o un valor del tipo de elemento.  
  
```  
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valarray o el valor de un tipo de elemento idéntico de la valarray del operando que se va a dividir, element-wise, la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son el cociente de elementos de la valarray operando dividido por ` right.`  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_ediv.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<double> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  100;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -100;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  2*i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL /= vaR;  
   cout << "The element-by-element result of "  
        << "the quotient is the\n valarray: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator_eq"></a>  valarray:: operator =  
 Asigna elementos a una valarray cuyos valores se especifican directamente o como parte de alguna otra valarray o por slice_array, gslice_array, mask_array o indirect_array.  
  
```  
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Valarray que se copiará en la valarray del operando.  
  
 ` val`  
 El valor que se asignará a los elementos de la valarray del operando.  
  
 `_Slicearray`  
 Slice_array que se copiará en la valarray del operando.  
  
 `_Gslicearray`  
 Gslice_array que se copiará en la valarray del operando.  
  
 `_Maskarray`  
 Mask_array que se copiará en la valarray del operando.  
  
 `_Indarray`  
 Indirect_array que se copiará en la valarray del operando.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer operador de miembro reemplaza la secuencia controlada por una copia de la secuencia controlada por ` right`.  
  
 El segundo operador de miembro es el mismo que la primera, pero con un [declarador de referencia Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 El tercer operador de miembro reemplaza cada elemento de la secuencia controlada por una copia de ` val`.  
  
 Los restantes operadores miembro reemplace los elementos de la secuencia controlada seleccionado por sus argumentos, que se generan solo [operador &#91; &#93;](#valarray__operator_at).  
  
 Si el valor de un miembro en la secuencia de reemplazo controlada depende de un miembro de la secuencia controlada inicial, el resultado es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si cambia la longitud de la secuencia controlada, el resultado es indefinido generalmente. En esta implementación, sin embargo, el efecto es simplemente invalidar los punteros o referencias a elementos de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_assign.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va [ i ] = i;  
   for ( i = 0 ; i < 10 ; i+=1 )  
      vaR [ i ] = 10 -  i;  
  
   cout << "The operand valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   cout << "The operand valarray vaR is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << vaR [ i ];  
   cout << endl;  
  
   // Assigning vaR to va with the first member functon  
   va = vaR;  
   cout << "The reassigned valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   // Assigning elements of value 10 to va  
   // with the second member functon  
   va = 10;  
   cout << "The reassigned valarray va is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << va [ i ];  
   cout << endl;  
}  
\* Output:   
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9  
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10  
*\  
```  
  
##  <a name="a-namevalarrayoperatorata-valarrayoperator"></a><a name="valarray__operator_at"></a>  [] valarray:: operator  
 Devuelve una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.  
  
```  
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

 
valarray<Type> operator[](slice _Slice) const;

 
valarray<Type> operator[](const gslice& _Gslicearray) const;

 
valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

 
valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 Índice del elemento que se va a asignar un valor.  
  
 `_Slicearray`  
 Slice_array de una valarray que especifica un subconjunto seleccionado o devuelto a una nueva valarray.  
  
 `_Gslicearray`  
 Gslice_array de una valarray que especifica un subconjunto seleccionado o devuelto a una nueva valarray.  
  
 *_Boolarray*  
 Un bool_array de una valarray que especifica un subconjunto seleccionado o devuelto a una nueva valarray.  
  
 `_Indarray`  
 Un indirect_array de una valarray que especifica un subconjunto seleccionado o devuelto a una nueva valarray.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.  
  
### <a name="remarks"></a>Comentarios  
 El operador de miembro se sobrecarga para proporcionar varios métodos para seleccionar secuencias de elementos entre los controlados por *\****Esto**. El primer grupo de operadores de cinco miembros funcionan en conjunción con varias sobrecargas de [operador =](#valarray__operator_eq) (y otros operadores de asignación) para permitir el reemplazo selectivo (segmentación) de la secuencia controlada. Deben existir los elementos seleccionados.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta obtener acceso a un elemento fuera de los límites de la valarray.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  Consulte los ejemplos de [slice:: Slice](../standard-library/slice-class.md#slice__slice) y [gslice:: gslice](../standard-library/gslice-class.md#gslice__gslice) para obtener un ejemplo de cómo declarar y utilizar el operador.  
  
##  <a name="a-namevalarrayoperatorxoreqa-valarrayoperator"></a><a name="valarray__operator_xor_eq"></a>  valarray:: operator ^ =  
 Obtiene el operador o exclusivo elementos lógico ( **XOR**) de una matriz con una valarray especificada o un valor del tipo de elemento.  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valor de un tipo de elemento idéntico de la valarray del operando que se pueden combinar, elementos por la lógica exclusiva o valarray **XOR** con la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son elementos, lógica exclusiva **XOR** de la valarray operando y ` right.`  
  
### <a name="remarks"></a>Comentarios  
 El exclusivo o lógico, que se conoce como **XOR**, tiene la semántica siguiente: dados elementos *e*1 y *e*2, *e*1 **XOR** *e*2 es **true** Si exactamente uno de los elementos es true; **false** Si ambos elementos son falsas o si ambos elementos son true.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_exor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL ^= vaR;  
   cout << "The element-by-element result of "  
        << "the bitwise XOR operator^= is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^= is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatororeqa-valarrayoperator124"></a><a name="valarray__operator_or_eq"></a>  valarray:: operator &#124; =  
 Obtiene el bit a bit `OR` de elementos de una matriz con los elementos correspondientes de una valarray especificado o con un valor del tipo de elemento.  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El valor de un tipo de elemento idéntico de la valarray del operando que se pueden combinar, elementos por bit a bit o valarray `OR` con la valarray de operando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una valarray cuyos elementos son los elementos de bit a bit `OR` de la valarray operando por ` right.`  
  
### <a name="remarks"></a>Comentarios  
 Una operación bit a bit sólo puede utilizarse para manipular los bits de `char` y `int` tipos de datos y sus variantes y no en **float**, **doble**, **longdouble**, `void`, `bool`, u otros, tipos de datos más complejos.  
  
 Bit a bit `OR` tiene la misma tabla de verdad que la lógica `OR` pero que se aplica al tipo de datos en el nivel de los bits individuales. Dados los bits *b*1 y *b*2, *b*1 `OR` *b*2 es **true** Si al menos uno de los bits es true; **false** Si ambos bits son falsas.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_class_op_bitor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL |= vaR;  
   cout << "The element-by-element result of "  
        << "the logical OR\n operator|= is the valarray:\n ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  
 ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is:  
 ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the logical OR  
 operator|= is the valarray:  
 ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatordtora-valarrayoperator"></a><a name="valarray__operator_dtor"></a>  valarray:: operator ~  
 Un operador unario que obtiene el bit a bit **NO** valores de cada elemento en una valarray.  
  
```  
valarray<Type> operator~() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La valarray de valores booleanos que son bit a bit **NO** de los valores de elemento de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 Una operación bit a bit sólo puede utilizarse para manipular los bits de `char` y `int` tipos de datos y sus variantes y no en **float**, **doble**, **longdouble**, `void`, `bool` u otros, tipos de datos más complejos.  
  
 Bit a bit **NO** tiene la misma tabla de verdad que la lógica **NO** pero que se aplica al tipo de datos en el nivel de los bits individuales. Dado el bit *b*, ~ *b* es true si *b* es false y false si *b* es true. La lógica **NO**[operador!](#valarray__operator_not) se aplica en un nivel de elemento, el recuento de todos los valores distintos de cero como **true**, y el resultado es una valarray de valores booleanos. Bit a bit **NOToperator ~**, por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_op_bitnot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<unsigned short int> vaL1 ( 10 );  
   valarray<unsigned short int> vaNOT1 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  5*i;  
  
   cout << "The initial valarray <unsigned short int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL1 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT1 = ~vaL1;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT1 [ i ] << " ";  
   cout << ")." << endl << endl;  
  
   valarray<int> vaL2 ( 10 );  
   valarray<int> vaNOT2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  -2 * i;  
  
   cout << "The initial valarray <int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL2 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT2 = ~vaL2;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // The negative numbers are represented using  
   // the two's complement approach, so adding one  
   // to the flipped bits returns the negative elements  
   vaNOT2 = vaNOT2 + 1;  
   cout << "The element-by-element result of "  
        << "adding one\n is the negative of the "  
        << "original elements the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).  
  
The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).  
The element-by-element result of adding one  
 is the negative of the original elements the  
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).  
*\  
```  
  
##  <a name="a-namevalarrayresizea-valarrayresize"></a><a name="valarray__resize"></a>  valarray:: Resize  
 Cambia el número de elementos de una valarray a un número especificado.  
  
```  
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,   
    const Type val);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Newsize`  
 Número de elementos de la valarray cuyo tamaño se cambió.  
  
 ` val`  
 Valor que se asignará a los elementos de la valarray cuyo tamaño se cambió.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro inicializa los elementos con su constructor predeterminado.  
  
 Se invalidan los punteros o referencias a elementos de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra cómo debe usarse la función miembro valarray::resize.  
  
```  
// valarray_resize.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, sizeNew;  
  
    valarray<int> va1(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray is: "  
         << size1  << "." <<endl << endl;  
  
    va1.resize(15, 10);  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 15; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
    sizeNew = va1.size();  
    cout << "The number of elements in the resized valarray is: "  
         << sizeNew  << "." <<endl << endl;  
}  
\* Output:   
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray is: 10.  
  
The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).  
The number of elements in the resized valarray is: 15.  
*\  
```  
  
##  <a name="a-namevalarrayshifta-valarrayshift"></a><a name="valarray__shift"></a>  valarray:: Shift  
 Desplaza todos los elementos en una valarray un número especificado de posiciones.  
  
```  
valarray<Type> shift(int count) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 El número de posiciones de los elementos es se desplace hacia adelante.  
  
### <a name="return-value"></a>Valor devuelto  
 Una nueva valarray en la que todos los elementos que se han movido ` count` posiciones hacia la parte delantera de la valarray, izquierda con respecto a sus posiciones en la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 Un valor positivo de ` count` los elementos a la izquierda se desplaza ` count` coloca con cero relleno.  
  
 Un valor negativo de ` count` se desplaza a la derecha de los elementos ` count` coloca con cero relleno.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_shift.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va1 ( 10 ), va2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va1 [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va2 [ i ] = 10 -  i;  
  
   cout << "The operand valarray va1(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A positive parameter shifts elements left  
   va1 = va1.shift ( 4 );  
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The operand valarray va2(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A negative parameter shifts elements right  
   va2 = va2.shift ( - 4 );  
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).  
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).  
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).  
*\  
```  
  
##  <a name="a-namevalarraysizea-valarraysize"></a><a name="valarray__size"></a>  valarray:: Size  
 Busca el número de elementos de una valarray.  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos de la valarray de operando.  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra cómo debe usarse la función miembro valarray::size.  
  
```  
// valarray_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, size2;  
  
    valarray<int> va1(10), va2(12);  
    for (i = 0; i < 10; i += 1)  
        va1[i] =  i;  
    for (i = 0; i < 10; i += 1)  
        va2[i] =  i;  
  
    cout << "The operand valarray va1(10) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray va1 is: va1.size = "  
         << size1  << "." <<endl << endl;  
  
    cout << "The operand valarray va2(12) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
  
    size2 = va2.size();  
    cout << "The number of elements in the valarray va2 is: va2.size = "  
         << size2  << "." << endl << endl;  
  
    // Initializing two more elements to va2  
    va2[10] = 10;  
    va2[11] = 11;  
    cout << "After initializing two more elements,\n "  
         << "the operand valarray va2(12) is now: ( ";  
        for (i = 0; i < 12; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
    cout << "The number of elements in the valarray va2 is still: "  
         << size2  << "." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va1 is: va1.size = 10.  
  
The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va2 is: va2.size = 12.  
  
After initializing two more elements,  
 the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).  
The number of elements in the valarray va2 is still: 12.  
*\  
```  
  
##  <a name="a-namevalarraysuma-valarraysum"></a><a name="valarray__sum"></a>  valarray:: Sum  
 Determina la suma de todos los elementos en una valarray de longitud distinta de cero.  
  
```  
Type sum() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La suma de los elementos de la valarray del operando.  
  
### <a name="remarks"></a>Comentarios  
 Si la longitud es mayor que uno, la función miembro agrega valores a la suma aplicando `operator+=` entre los pares de elementos de la clase **tipo**, qué operador, por lo tanto, debe proporcionarse para elementos de tipo **tipo**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_sum.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   int sumva = 0;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va (10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sumva = va.sum ( );  
   cout << "The sum of elements in the valarray is: "  
        << sumva  << "." <<endl;  
}  
\* Output:   
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The sum of elements in the valarray is: 45.  
*\  
```  
  
##  <a name="a-namevalarrayswapa-valarrayswap"></a><a name="valarray__swap"></a>  valarray:: swap  
 Intercambia los elementos de dos `valarray`.  
  
```  
void swap(valarray& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|` right`|`valarray` que proporciona los elementos que se van a intercambiar.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia las secuencias controladas entre `*this` y ` right`. Lo hace en tiempo constante, no inicia ninguna excepción y no invalida ninguna referencia, puntero o iterador que designen elementos en las dos secuencias controladas.  
  
##  <a name="a-namevalarrayvalarraya-valarrayvalarray"></a><a name="valarray__valarray"></a>  valarray:: valarray  
 Construye una valarray de un tamaño específico o con elementos de un valor determinado, o como una copia de otra valarray o un subconjunto de otra valarray.  
  
```  
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,   
    size_t Count);

valarray(
    const Type* Ptr,   
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```  
  
### <a name="parameters"></a>Parámetros  
 `Count`  
 Número de elementos que va a haber en la valarray.  
  
 `Val`  
 Valor que se utilizará al inicializar los elementos de la valarray.  
  
 `Ptr`  
 Puntero a los valores que se usarán para inicializar los elementos de la valarray.  
  
 `Right`  
 Valarray existente para inicializar la nueva valarray.  
  
 `SliceArray`  
 slice_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.  
  
 `GsliceArray`  
 gslice_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.  
  
 `MaskArray`  
 mask_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.  
  
 `IndArray`  
 indirect_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.  
  
 `IList`  
 initializer_list que contiene los elementos que se van a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor (predeterminado) inicializa el objeto en una matriz vacía. Cada uno de los tres constructores siguientes inicializan el objeto en una matriz de elementos `Count` de la manera siguiente:  
  
-   En el caso de `valarray(size_t Count)` explícito, cada elemento se inicializa con el constructor predeterminado.  
  
-   En `valarray(const Type& Val, Count)`, cada elemento se inicializa con `Val`.  
  
-   Para `valarray(const Type* Ptr, Count)`, el elemento en la posición `I` se inicializa con `Ptr`[ `I`].  
  
 Cada constructor restante inicializa el objeto en una valarray \< tipo> determinado por el subconjunto especificado en el argumento de objeto.  
  
 El último constructor es igual a junto al último, pero con un [declarador de referencia Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    // The second member function  
    valarray<int> va(10);  
    for (auto i : va){  
        va[i] = 2 * (i + 1);  
    }  
  
    cout << "The operand valarray va is:\n(";  
    for (auto i : va) {  
        cout << " " << va[i];  
    }  
    cout << " )" << endl;  
  
    slice Slice(2, 4, 3);  
  
    // The fifth member function  
    valarray<int> vaSlice = va[Slice];  
  
    cout << "The new valarray initialized from the slice is vaSlice ="  
        << "\nva[slice( 2, 4, 3)] = (";  
    for (int i = 0; i < 3; i++) {  
        cout << " " << vaSlice[i];  
    }  
    cout << " )" << endl;  
  
    valarray<int> va2{{ 1, 2, 3, 4 }};  
    for (auto& v : va2){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4  
```  
  
##  <a name="a-namevalarrayvaluetypea-valarrayvaluetype"></a><a name="valarray__value_type"></a>  valarray:: value_type  
 Tipo que representa el tipo de elemento almacenado en una valarray.  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **tipo**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// valarray_value_type.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // value_type declaration and initialization:  
   valarray<int>::value_type Right = 10;  
  
   cout << "The decalared value_type Right is: "   
           << Right << endl;  
   va *= Right;  
   cout << "The resulting valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The decalared value_type Right is: 10  
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).  
*\  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

