---
title: Constructores de copia y operadores de asignación de copia (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5b1843331afc6fa686446e7b3d7515d8701b9cf
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026216"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Constructores de copia y operadores de asignación de copia (C++)
> [!NOTE]
>  A partir de C ++ 11, se admiten dos tipos de asignación en el lenguaje: *Copiar asignación* y *asignación de movimiento*. En este artículo, "asignación" significa asignación de copia a menos que se establezca explícitamente lo contrario. Para obtener información acerca de la asignación de movimiento, consulte [constructores de movimiento y operadores de asignación de movimiento (C++)](http://msdn.microsoft.com/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Tanto la operación de asignación como la operación de inicialización provocan que los objetos se copien.  
  
-   **Asignación**: cuando se asigna el valor de un objeto a otro objeto, el primer objeto se copia en el segundo objeto. Por lo tanto,  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     hace que el valor de `b` se copie en `a`.  
  
-   **Inicialización**: la inicialización se produce cuando se declara un nuevo objeto, cuando se pasan argumentos a funciones por valor, o cuando se devuelven los valores de las funciones por valor.  
  
 Puede definir la semántica de “copy” para los objetos de tipo de clase. Por ejemplo, considere este código:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 El código anterior podría significar “copiar el contenido de FILE1.DAT en FILE2.DAT” o podría significar “omitir FILE2.DAT y convertir `b` en un segundo identificador para FILE1.DAT”. Debe asociar la semántica de copia correspondiente a cada clase, de la manera siguiente.  
  
-   Mediante el operador de asignación **operador =** junto con una referencia al tipo de clase como el tipo de valor devuelto y el parámetro que se pasa por **const** referencia — por ejemplo `ClassName& operator=(const ClassName& x);`.  
  
-   Utilizando el constructor de copias.   
  
 Si no declara un constructor de copias, el compilador genera uno automáticamente miembro a miembro.  Si no declara una asignación de copia, el compilador genera una automáticamente miembro a miembro. Declarar un constructor de copias no suprime el operador de asignación de copias generado por el compilador, ni viceversa. Si se implementa cualquiera de ellos, es recomendable implementar también el otro de modo que el significado del código esté claro.  
   
 El constructor de copias toma un argumento de tipo * clase-nombre ***&**, donde *nombre de la clase* es el nombre de la clase para el que se define el constructor. Por ejemplo:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Convierta el tipo de argumento del constructor de copia *clase const-nombre *** &** siempre que sea posible. Esto evita que el constructor de copias modifique accidentalmente el objeto del que se está copiando. También permite copiar de **const** objetos.  
  
## <a name="compiler-generated-copy-constructors"></a>Constructores de copias generados por el compilador  
 Constructores de copias generado por el compilador, como constructores de copias definido por el usuario, tienen un único argumento de tipo "referencia a *nombre de la clase*." Una excepción es cuando todas las clases bases y miembro tienen constructores de copias declarados de modo que toman un único argumento de tipo **const** * clase-nombre ***&**. En tal caso, el argumento del constructor de copias generado por el compilador también es **const**.  
  
 Cuando el tipo de argumento al constructor de copias no es **const**, inicialización copiando un **const** objeto genera un error. Lo contrario no es cierto: si el argumento es **const**, puede inicializar copiando un objeto que no es **const**.  
  
 Operadores de asignación generados por el compilador siguen el mismo patrón con respecto a **const.** Toman un solo argumento de tipo *clase-nombre *** &** a menos que los operadores de asignación en todas las clases base y miembro tomen argumentos de tipo **const** *clase-name &.* En este caso, la clase generado de la asignación operador toma un **const** argumento.  
  
> [!NOTE]
>  Cuando los constructores de copias, generados por el compilador o definidos por el usuario, inicializan las clases base virtuales, estas se inicializan solo una vez: en el momento en que se construyen.  
  
 Las implicaciones son similares a las del constructor de copias. Cuando el tipo de argumento no es **const**, asignación de un **const** objeto genera un error. Lo contrario no es cierto: si un **const** valor se asigna a un valor que no es **const**, la asignación se realiza correctamente.  
  
 Para obtener más información acerca de los operadores de asignaciones sobrecargados, vea [asignación](../cpp/assignment.md).  
  
