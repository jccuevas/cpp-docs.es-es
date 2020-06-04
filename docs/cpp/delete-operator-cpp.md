---
title: delete (Operador) (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 2ffb307aa3eb6bb8d253129a550c95342ad497bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189473"
---
# <a name="delete-operator-c"></a>delete (Operador) (C++)

Desasigna un bloque de memoria.

## <a name="syntax"></a>Sintaxis

> [`::`] `delete` *Cast-expression*\
> [`::`] `delete []` *Cast-Expression*

## <a name="remarks"></a>Observaciones

El argumento *Cast-Expression* debe ser un puntero a un bloque de memoria previamente asignado para un objeto creado con el [operador New](../cpp/new-operator-cpp.md). El operador **Delete** tiene un resultado de tipo **void** y, por lo tanto, no devuelve un valor. Por ejemplo:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

El uso de **Delete** en un puntero a un objeto no asignado con **New** proporciona resultados imprevisibles. Sin embargo, puede usar **Delete** en un puntero con el valor 0. Esta disposición significa que, cuando **New** devuelve 0 en caso de error, es inofensivo eliminar el resultado de una operación **New** con errores. Para obtener más información, vea [los operadores New y DELETE](../cpp/new-and-delete-operators.md).

Los operadores **New** y **Delete** también se pueden usar para los tipos integrados, incluidas las matrices. Si `pointer` hace referencia a una matriz, coloque corchetes vacíos (`[]`) antes `pointer`:

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

El uso del operador **Delete** en un objeto desasigna su memoria. Un programa que desreferencia un puntero después de eliminarse el objeto puede producir resultados impredecibles o bloquearse.

Cuando se utiliza **Delete** para desasignar memoria para un C++ objeto de clase, se llama al destructor del objeto antes de que se cancele la asignación de la memoria del objeto (si el objeto tiene un destructor).

Si el operando del operador **Delete** es un valor l modificable, su valor es undefined una vez eliminado el objeto.

Si se especifica la opción del compilador [/SDL (habilitar comprobaciones de seguridad adicionales)](/cpp/build/reference/sdl-enable-additional-security-checks) , el operando del operador **Delete** se establece en un valor no válido después de que se elimine el objeto.

## <a name="using-delete"></a>Usar delete

Hay dos variantes sintácticas para el [operador Delete](../cpp/delete-operator-cpp.md): una para objetos individuales y la otra para matrices de objetos. En el fragmento de código siguiente se muestra cómo difieren:

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

Los dos casos siguientes producen resultados sin definir: usar la forma de matriz de Delete (`delete []`) en un objeto y usar la forma de no matriz de DELETE en una matriz.

## <a name="example"></a>Ejemplo

Para obtener ejemplos del uso de **Delete**, vea [New (operador](../cpp/new-operator-cpp.md)).

## <a name="how-delete-works"></a>Cómo eliminar trabajos

El operador Delete invoca la función de **operador Delete**.

Para los objetos que no son de tipo de clase ([Class](../cpp/class-cpp.md), [struct](../cpp/struct-cpp.md)o [Union](../cpp/unions.md)), se invoca el operador Delete global. Para los objetos de tipo de clase, el nombre de la función de desasignación se resuelve en el ámbito global si la expresión de eliminación comienza con el operador unario de resolución de ámbito (`::`). Si no, el operador delete invoca el destructor de un objeto antes de la desasignación de memoria (si el puntero no es nulo). El operador delete puede definirse clase por clase; si no existe esta definición para una clase determinada, se invoca el operador delete global. Si la expresión de eliminación se utiliza para desasignar un objeto de clase cuyo de tipo estático tenga un destructor virtual, la función de desasignación se resuelve mediante el destructor virtual del tipo dinámico del objeto.

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)\
[Palabras clave](../cpp/keywords-cpp.md)\
[Operadores new y delete](../cpp/new-and-delete-operators.md)
