---
title: static_cast (operador) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9af76787780ebe2a25b3fab46ce1951085b8e8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944768"
---
# <a name="staticcast-operator"></a>static_cast (Operador)
Convierte un *expresión* al tipo de *type_id,* basándose únicamente en los tipos que se encuentran en la expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>Comentarios  
 En Standard C++, no se realiza ninguna comprobación de tipo en tiempo de ejecución como ayuda para garantizar la seguridad de la conversión. En C++/CX, se realiza una comprobación en tiempo de compilación y en tiempo de ejecución. Para obtener más información, consulte [conversión](casting.md).  
  
 El **static_cast** operador puede usarse para realizar operaciones como convertir un puntero a una clase base a un puntero a una clase derivada. Estas conversiones no siempre son seguras.  
  
 En general utilice **static_cast** algunos de los tipos de datos cuando desee convertir tipos de datos numéricos como enumeraciones en enteros o valores de tipo int en flotantes y están implicados en la conversión. **static_cast** conversiones no son tan seguras como **dynamic_cast** conversiones, porque **static_cast** ningún tipo de tiempo de ejecución comprueba, mientras **dynamic_cast** lo hace. Un **dynamic_cast** a un puntero ambiguo producirá un error, mientras que un **static_cast** devuelve como si hubiera nada incorrecto; Esto puede ser peligroso. Aunque **dynamic_cast** conversiones son más seguras, **dynamic_cast** solo funciona en punteros o referencias y la comprobación del tipo de tiempo de ejecución es una sobrecarga. Para obtener más información, consulte [dynamic_cast (operador)](../cpp/dynamic-cast-operator.md).  
  
 En el ejemplo siguiente, la línea `D* pd2 = static_cast<D*>(pb);` no es segura porque `D` puede tener campos y métodos que no están en `B`. Sin embargo, la línea `B* pb2 = static_cast<B*>(pd);` es una conversión segura porque `D` siempre contiene todo `B`.  
  
```cpp 
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 En contraposición al [dynamic_cast](../cpp/dynamic-cast-operator.md), se realiza ninguna comprobación de tiempo de ejecución en el **static_cast** conversión de `pb`. El objeto al que apunta `pb` puede no ser un objeto de tipo `D`, en cuyo caso el uso de `*pd2` podría ser desastroso. Por ejemplo, la llamada a una función que es miembro de la clase `D`, pero no de la clase `B`, podría producir una infracción de acceso.  
  
 El **dynamic_cast** y **static_cast** operadores mueven un puntero en una jerarquía de clases. Sin embargo, **static_cast** se basa exclusivamente en la información proporcionada en la instrucción de conversión y, por tanto, puede no ser seguro. Por ejemplo:  
  
```cpp 
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 Si `pb` apunta realmente un objeto de tipo `D`, `pd1` y `pd2` obtienen el mismo valor. También obtienen el mismo valor si `pb == 0`.  
  
 Si `pb` apunta a un objeto de tipo `B` y no a toda `D` clase y luego **dynamic_cast** sabe suficiente para devolver cero. Sin embargo, **static_cast** se basa en la aserción del programador que `pb` apunta a un objeto de tipo `D` y simplemente devuelve un puntero a la que supone `D` objeto.  
  
 Por lo tanto, **static_cast** puede realizar la operación inversa de las conversiones implícitas, en cuyo caso los resultados son indefinidos. Se deja al programador para comprobar que los resultados de una **static_cast** conversión son seguros.  
  
 Este comportamiento también se aplica a los tipos distintos de los tipos de clase. Por ejemplo, **static_cast** puede usarse para convertir de int a un **char**. Sin embargo, el resultado **char** no tenga suficientes bits para almacenar toda la **int** valor. De nuevo, se deja al programador para comprobar que los resultados de una **static_cast** conversión son seguros.  
  
 El **static_cast** operador también puede utilizarse para realizar cualquier conversión implícita, incluidas las conversiones estándar y conversiones definidas por el usuario. Por ejemplo:  
  
```cpp 
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 El **static_cast** operador puede convertir explícitamente un valor entero a un tipo de enumeración. Si el valor del tipo entero no está dentro del intervalo de valores de enumeración, el valor de enumeración resultante no está definido.  
  
 El **static_cast** operador convierte un valor de puntero nulo en el valor de puntero null del tipo de destino.  
  
 Cualquier expresión se puede convertir explícitamente al tipo void el **static_cast** operador. El tipo void de destino puede incluir opcionalmente el **const**, **volátil**, o **__unaligned** atributo.  
  
 El **static_cast** operador no se puede desechar el **const**, **volátil**, o **__unaligned** atributos. Consulte [const_cast (operador)](../cpp/const-cast-operator.md) para obtener información acerca de cómo quitar estos atributos.  
  
 Debido al riesgo que supone realizar conversiones no comprobadas en la parte superior de una reubicación recolector de elementos no utilizados, el uso de **static_cast** solo debe utilizarse en código crítico para el rendimiento cuando esté seguro de funcionará correctamente. Si debe usar **static_cast** en modo de lanzamiento, sustitúyalo con [safe_cast](../windows/safe-cast-cpp-component-extensions.md) en las compilaciones de depuración para garantizar el éxito.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de conversión](../cpp/casting-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)