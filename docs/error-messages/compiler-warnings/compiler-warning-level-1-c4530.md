---
title: Advertencia del compilador (nivel 1) C4530
description: Guía de referencia para la advertencia del compilador C4530 de Microsoft C++ .
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369783"
---
# <a name="compiler-warning-level-1-c4530"></a>Advertencia del compilador (nivel 1) C4530

> Se usa el controlador de excepciones C++, pero la semántica de desenredo no está habilitada. Especificar /EHsc

El código usa el control de excepciones de C++, pero [/EHsc](../../build/reference/eh-exception-handling-model.md) no se incluyó en las opciones del compilador.

## <a name="remarks"></a>Observaciones

El compilador requiere **`/EHsc`** la opción para compilar código C++ que sigue el estándar C++ para el control de excepciones. La semántica de *desenredo* estándar de C++ especifica que los objetos y los marcos de pila construidos entre donde se produce una excepción y dónde se detecta deben destruirse y recuperarse sus recursos. Este proceso se conoce como *desenredar la pila.*

La **`/EHsc`** opción indica al compilador que genere código que llame a los destructores en objetos de almacenamiento automático cuando una excepción pasa a través del marco de pila contenedor. *Los* objetos de almacenamiento automático son objetos asignados en la pila, como variables locales. Se denomina almacenamiento automático porque se asigna automáticamente cuando se llama a las funciones y se libera automáticamente cuando se devuelven. Un marco de *pila* son los datos colocados en la pila cuando se llama a una función, junto con su almacenamiento automático.

Cuando se produce una excepción, puede viajar a través de varios marcos de pila antes de que se detecte. Estos marcos de pila deben desenrollarse a medida que la excepción pasa a través de ellos en orden de llamada inverso. Los objetos de almacenamiento automático en cada marco de pila deben destruirse para recuperar sus recursos de forma limpia. Es el mismo proceso de destrucción y recuperación que se produce automáticamente cuando una función vuelve normalmente.

Cuando **`/EHsc`** la opción no está habilitada, los objetos de almacenamiento automático en los marcos de pila entre la función de lanzamiento y la función donde se detecta la excepción no se destruyen. Solo se destruyen los objetos de almacenamiento automático creados en un bloque **try** o **catch,** lo que puede provocar fugas significativas de recursos y otros comportamientos inesperados.

Si es posible que no se produzcan excepciones en el ejecutable, puede omitir esta advertencia de forma segura. Algunos códigos pueden requerir otras opciones de control de excepciones. Para obtener más información, consulte [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compile el **`/EHsc`** ejemplo con para resolver la advertencia.
