---
title: Funciones de &lt;utility&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: d2b444c2de41651ac74047717ed54a7059866f86
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="ltutilitygt-functions"></a>Funciones de &lt;utility&gt;
||||  
|-|-|-|  
|[exchange](#exchange)|[forward](#forward)|[get (función) &lt;utility&gt;](#get)|  
|[make_pair](#make_pair)|[move](#move)|[swap](#swap)|  
  
##  <a name="exchange"></a>  exchange  
 **(C++14)** Asigna un nuevo valor a un objeto y devuelve su valor anterior.  
  
```cpp  
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 El objeto que va a recibir el valor de new_val.  
  
 `new_val`  
 El objeto cuyo valor se ha copiado o movido a val.  
  
### <a name="remarks"></a>Comentarios  
 Para los tipos complejos, `exchange` evita copiar el valor anterior cuando está disponible un constructor de movimiento, evita copiar el valor nuevo si es un objeto temporal o si se mueve, y acepta cualquier tipo como el valor nuevo, utilizando cualquier operador de asignación y conversión disponible. La función exchange es diferente de [std::swap](../standard-library/algorithm-functions.md#swap) en cuanto a que el argumento izquierdo no se mueve ni se copia en el argumento derecho.  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra cómo utilizar `exchange`. En el mundo real, `exchange` resulta más útil con objetos grandes que cuesta mucho copiar:  
  
```  
#include <utility>  
#include <iostream>  
  
using namespace std;  
  
struct C  
{  
int i;  
//...  
};  
int main()  
{     
// Use brace initialization   
C c1{ 1 };  
C c2{ 2 };  
C result = exchange(c1, c2);  
cout << "The old value of c1 is: " << result.i << endl;  
cout << "The new value of c1 after exchange is: " << c1.i << endl;  
  
return 0;  
}  
/* Output:  
The old value of c1 is: 1  
The new value of c1 after exchange is: 2  
*/  
```  
  
##  <a name="forward"></a>  forward  
 Convierte condicionalmente su argumento a una referencia de valor R si el argumento es un valor R o una referencia de valor R. Esto restaura el valor R de un argumento a la función de reenvío para permitir el reenvío directo.  
  
```
template <class Type>    // accepts lvalues
constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|Tipo del valor pasado en `Arg`, que puede ser diferente que el tipo de `Arg`. Lo suele determinar un argumento de plantilla de la función de reenvío.|  
|`Arg`|Argumento que se va a convertir.|  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia de valor R a `Arg` si el valor pasado en `Arg` era originalmente un valor R o una referencia a un valor R; de lo contrario, devuelve `Arg` sin modificar su tipo.  
  
### <a name="remarks"></a>Comentarios  
 Debe especificar un argumento de plantilla explícito para llamar a `forward`.  
  
 `forward` no reenvía su argumento. En su lugar, convirtiendo condicionalmente su argumento a una referencia de valor R si era originalmente un valor R o una referencia de valor R, `forward` permite al compilador realizar la resolución de sobrecargas conociendo del tipo original del argumento reenviado. Es posible que el tipo aparente de un argumento de una función de reenvío sea diferente de su tipo original, por ejemplo, cuando se usa un valor R como argumento de una función y se enlaza a un nombre de parámetro. Si tiene un nombre se convierte en un valor L, independientemente de que el valor exista realmente como un valor R. `forward` restaura el valor R del argumento.  
  
 Restaurar el valor R del valor original de un argumento para realizar la resolución de sobrecargas se denomina *reenvío directo*. El reenvío directo permite que una función de plantilla acepte un argumento de cualquier tipo de referencia y restaure su valor R cuando sea necesario para la correcta resolución de sobrecargas. Mediante el reenvío directo, se puede conservar la semántica de movimiento para los valores R y evitar tener que proporcionar sobrecargas para las funciones que solo varían por el tipo de referencia de sus argumentos.  
  
##  <a name="get"></a>  get  
 Obtiene un elemento de un objeto `pair` , por posición de índice o por tipo.  
  
```
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&
get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr const tuple_element_t<Index, pair<T1, T2>>&
get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&&
get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Index`  
 El índice de base 0 del elemento designado.  
  
 `T1`  
 El tipo del primer elemento par.  
  
 `T2`  
 El tipo del segundo elemento par.  
  
 `pr`  
 Par del que se selecciona.  
  
### <a name="remarks"></a>Comentarios  
 Las funciones de plantilla devuelven una referencia a un elemento de su argumento `pair` .  
  
 En el caso de sobrecargas indexadas, si el valor de `Index` es 0, las funciones devuelven `pr.first` y si el valor de `Index` es 1, las funciones devuelven `pr.second`. El tipo `RI` es el tipo del elemento devuelto.  
  
 En el caso de las sobrecargas que no tienen un parámetro de índice, el elemento para devolver se deduce mediante el argumento de tipo. Al llamar a `get<T>(Tuple)` , se producirá un error de compilador si `pr` contiene más o menos de un elemento de tipo T.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
#include <utility>  
#include <iostream>   
using namespace std;  
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index  
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)  
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```  
  
##  <a name="make_pair"></a>  make_pair  
 Una función de plantilla que se usa para construir objetos de tipo `pair`, donde los tipos de componente se eligen automáticamente basándose en los tipos de datos que se pasan como parámetros.  
  
```
template <class T, class U>
pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U&& Val2);
```  
  
### <a name="parameters"></a>Parámetros  
 `Val1`  
 Valor que inicializa el primer elemento de `pair`.  
  
 `Val2`  
 Valor que inicializa el segundo elemento de `pair`.  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de par que se construye: `pair`< `T`, `U`>( `Val1`, `Val2`).  
  
### <a name="remarks"></a>Comentarios  
 `make_pair` convierte el objeto de tipo [reference_wrapper (Clase)](../standard-library/reference-wrapper-class.md) en tipos de referencia y convierte las matrices y las funciones que decaen en punteros.  
  
 En el objeto `pair` devuelto, `T` se determina como sigue:  
  
-   Si el tipo de entrada `T` es `reference_wrapper<X>`, el tipo devuelto `T` es `X&`.  
  
-   De lo contrario, el tipo devuelto `T` es `decay<T>::type`. Si no se admite [decay (Clase)](../standard-library/decay-class.md), el tipo devuelto `T` es igual que el tipo de entrada `T`.  
  
 El tipo devuelto `U` se determina de igual forma a partir del tipo de entrada `U`.  
  
 Una ventaja de `make_pair` es que el compilador determina automáticamente los tipos de objetos que se almacenan y no tienen que especificarse explícitamente. No utilice los argumentos de plantilla explícitos como `make_pair<int, int>(1, 2)` cuando use `make_pair` porque es innecesariamente detallado y agrega problemas complejos de referencia rvalue que pueden producir un error de compilación. En este ejemplo, la sintaxis correcta sería `make_pair(1, 2)`.  
  
 La función auxiliar `make_pair` también permite pasar dos valores a una función que requiera un par como un parámetro de entrada.  
  
### <a name="example"></a>Ejemplo  
  Para obtener un ejemplo sobre cómo usar la función auxiliar `make_pair` para declarar e inicializar un par, vea [pair (Estructura)](../standard-library/pair-structure.md).  
  
##  <a name="move"></a>  move  
 Convierte incondicionalmente su argumento en una referencia rvalue y de este modo indica que se puede mover si su tipo tiene habilitado el movimiento.  
  
```
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|Un tipo inferido a partir del tipo del argumento pasado en `Arg`, junto con las reglas de contracción de referencias.|  
|`Arg`|Argumento que se va a convertir. Aunque el tipo de `Arg` parece estar especificado como una referencia rvalue, `move` también acepta argumentos lvalue porque las referencias lvalue pueden enlazarse con las referencias rvalue.|  
  
### <a name="return-value"></a>Valor devuelto  
 `Arg` como referencia rvalue, independientemente de si su tipo es un tipo de referencia.  
  
### <a name="remarks"></a>Comentarios  
 El argumento de plantilla `Type` no está pensado para especificarse explícitamente, sino para deducirse a partir del tipo del valor pasado en `Arg`. El tipo de `Type` se ajusta más en función de las reglas de contracción de referencias.  
  
 `move` no mueve su argumento. En lugar de esto, al convertir incondicionalmente su argumento (que podría ser un lvalue) en una referencia rvalue, permite al compilador mover posteriormente, en lugar de copiar, el valor pasado en `Arg` si su tipo tiene habilitado el movimiento. Si su tipo no tiene habilitado el movimiento, se copia.  
  
 Si el valor pasado en `Arg` es lvalue (es decir, tiene nombre o se puede tomar su dirección), se invalida cuando se produce el movimiento. No haga referencia al valor pasado en `Arg` por su nombre o dirección una vez que se haya movido.  
  
##  <a name="swap"></a>  swap  
 Intercambia los elementos de dos objetos [pair (Estructura)](../standard-library/pair-structure.md).  
  
```
template <class T, class U>  
void swap(pair<T, U>& left, pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `pair`.|  
|`right`|Objeto de tipo `pair`.|  
  
### <a name="remarks"></a>Comentarios  
 Una ventaja de `swap` es que el compilador determina automáticamente los tipos de objetos que se almacenan y no tienen que especificarse explícitamente. No utilice los argumentos de plantilla explícitos como `swap<int, int>(1, 2)` cuando use `swap` porque es innecesariamente detallado y agrega problemas complejos de referencia rvalue que pueden producir un error de compilación.  
  
## <a name="see-also"></a>Vea también  
 [\<utility>](../standard-library/utility.md)




