---
title: delete (Operador) (C++)
ms.date: 11/04/2016
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 5e4f5685ea1bb8cd7c405373ba774fe36af08672
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398971"
---
# <a name="delete-operator-c"></a>delete (Operador) (C++)

Desasigna un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```
[::] delete cast-expression
[::] delete [ ] cast-expression
```

## <a name="remarks"></a>Comentarios

El *unary-expression* argumento debe ser un puntero a un bloque de memoria asignado previamente para un objeto creado con la [nuevo operador](../cpp/new-operator-cpp.md). El **eliminar** operador tiene un resultado de tipo **void** y, por tanto, no devuelve un valor. Por ejemplo:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

Uso de **eliminar** en un puntero a un objeto no asignado con **nuevo** tiene resultados impredecibles. Sin embargo, puede usar **eliminar** en un puntero con el valor 0. Este aprovisionamiento significa que, cuando **nueva** devuelve 0 en caso de error al eliminar el resultado de un error **nuevo** operación es inofensiva. Consulte [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md) para obtener más información.

El **nueva** y **eliminar** operadores también se pueden usar para los tipos integrados, incluidas las matrices. Si `pointer` hace referencia a una matriz, ponga corchetes vacíos delante de `pointer`:

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

Mediante el **eliminar** operador en un objeto desasigna su memoria. Un programa que desreferencia un puntero después de eliminarse el objeto puede producir resultados impredecibles o bloquearse.

Cuando **eliminar** es utiliza para desasignar memoria para un objeto de clase de C++, se llama al destructor del objeto antes de la memoria del objeto se desasigna (si el objeto tiene un destructor).

Si el operando situado a la **eliminar** operador es un valor l modificable, su valor no está definido después de elimina el objeto.

## <a name="using-delete"></a>Usar delete

Hay dos variantes sintácticas para el [delete (operador)](../cpp/delete-operator-cpp.md): uno para objetos individuales y otro para las matrices de objetos. En el fragmento de código siguiente se muestra cómo difieren entre sí:

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

Los dos casos siguientes generan resultados sin definir: usando la forma de matriz de (delete [ ]) en un objeto y usando la forma no de matriz de delete en una matriz.

## <a name="example"></a>Ejemplo

Para obtener ejemplos del uso de **eliminar**, consulte [nuevo operador](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Cómo eliminar trabajos

El operador delete invoca la función **operador delete**.

Para los objetos no es del tipo de clase ([clase](../cpp/class-cpp.md), [struct](../cpp/struct-cpp.md), o [unión](../cpp/unions.md)), se invoca el operador delete global. Para los objetos de tipo de clase, el nombre de la función de desasignación se resuelve en el ámbito global si la expresión de eliminación comienza con el operador unario de resolución de ámbito (::). Si no, el operador delete invoca el destructor de un objeto antes de la desasignación de memoria (si el puntero no es nulo). El operador delete puede definirse clase por clase; si no existe esta definición para una clase determinada, se invoca el operador delete global. Si la expresión de eliminación se utiliza para desasignar un objeto de clase cuyo de tipo estático tenga un destructor virtual, la función de desasignación se resuelve mediante el destructor virtual del tipo dinámico del objeto.

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Operadores new y delete](../cpp/new-and-delete-operators.md)