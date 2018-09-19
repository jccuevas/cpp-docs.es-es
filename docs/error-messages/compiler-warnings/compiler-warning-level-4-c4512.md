---
title: Del compilador (nivel 4) de la advertencia C4512 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aee9e7f48430ddc9b2b9a6a7f055ac8b1e32b71
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029954"
---
# <a name="compiler-warning-level-4-c4512"></a>Advertencia del compilador (nivel 4) C4512

'clase': no se pudo generar el operador de asignación

El compilador no puede generar un operador de asignación para la clase dada. No se ha creado ningún operador de asignación.

Esta advertencia puede deberse a un operador de asignación para la clase base que no es accesible a la clase derivada.

Para evitar esta advertencia, especifique para la clase un operador de asignación definido por el usuario.

El compilador también generará una función de operador de asignación para una clase que no tenga uno definido. Este operador de asignación es una copia miembro a miembro de los miembros de datos de un objeto. Dado que los elementos de datos `const` no se pueden modificar después de la inicialización, si la clase contiene un elemento `const`, el operador de asignación predeterminado no funcionará. Otra causa de la advertencia C4512 es una declaración de un miembro de datos no estáticos de tipo de referencia. Si la intención es crear un tipo que no se pueda copiar, debe evitar también la creación de un constructor de copias predeterminado.

Puede resolver la advertencia C4512 para el código de una de estas tres maneras:

- Defina explícitamente un operador de asignación para la clase.

- Quitar **const** o el operador de referencia de elemento de datos de la clase.

- Utilice #pragma [advertencia](../../preprocessor/warning.md) instrucción para suprimir la advertencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4512.

```
// C4512.cpp
// compile with: /EHsc /W4
// processor: x86

class Base {
private:
   const int a;

public:
   Base(int val = 0) : a(val) {}
   int get_a() { return a; }
};   // C4512 warning

class Base2 {
private:
   const int a;

public:
   Base2(int val = 0) : a(val) {}
   Base2 & operator=( const Base2 & ) { return *this; }
   int get_a() { return a; }
};

// Type designer intends this to be non-copyable because it has a
// reference member
class Base3
{
private:
   char& cr;

public:
   Base3(char& r) : cr(r) {}
   // Uncomment the following line to explicitly disable copying:
   // Base3(const Base3&) = delete;
};   // C4512 warning

int main() {
   Base first;
   Base second;

   // OK
   Base2 first2;
   Base2 second2;

   char c = 'x';
   Base3 first3(c);
   Base3 second3 = first3; // C2280 if no default copy ctor
}
```