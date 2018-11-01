---
title: Advertencia del compilador (nivel 1) C4743
ms.date: 11/04/2016
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: d17fd65f1108aab6e3ce97ec75c0ffb899c06cda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441852"
---
# <a name="compiler-warning-level-1-c4743"></a>Advertencia del compilador (nivel 1) C4743

'*tipo*'tiene un tamaño diferente '*file1*'y'*file2*': *número* y *número* bytes

Una variable externa que hace referencia o definido en dos archivos tiene distintos tipos de esos archivos, y el compilador determina que el tamaño de la variable en *file1* difiere del tamaño de la variable en *file2*.

Es importante cuando esta advertencia se puede emitir para C++. Si declara los mismos tipos con el mismo nombre en dos archivos distintos, si estas declaraciones contienen funciones virtuales, y si las declaraciones no son iguales, el compilador puede emitir advertencia C4744 para las tablas de la función virtual. La advertencia se produce porque hay dos tablas de la función virtual de tamaño diferente para el mismo tipo y el vinculador debe elegir uno de ellos para incorporar en el archivo ejecutable.  Es posible que esto puede producir en el programa llame a la función virtual equivocada.

Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para los tipos o variables.

## <a name="example"></a>Ejemplo

Este ejemplo contiene una definición del tipo.

```
// C4743a.cpp
// compile with: /c
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4743.

```
// C4743b.cpp
// compile with: C4743a.cpp /W1 /GL /O2
// C4743 expected
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```