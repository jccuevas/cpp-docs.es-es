---
title: Advertencia del compilador (nivel 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611828"
---
# <a name="compiler-warning-level-1-c4743"></a>Advertencia del compilador (nivel 1) C4743

'*tipo*'tiene un tamaño diferente '*file1*'y'*file2*': *número* y *número* bytes

Una variable externa que hace referencia o definido en dos archivos tiene distintos tipos de esos archivos, y el compilador determina que el tamaño de la variable en *file1* difiere del tamaño de la variable en *file2*.

## <a name="remarks"></a>Comentarios

Hay un caso importante cuando esta advertencia se puede emitir para C++. Si declara los mismos tipos con el mismo nombre en dos archivos distintos, si estas declaraciones contienen funciones virtuales, y si las declaraciones no son iguales, el compilador puede emitir advertencia C4744 para las tablas de la función virtual. La advertencia se produce porque hay dos tablas diferentes tamaños de función virtual para el mismo tipo y el vinculador debe elegir uno de ellos para incorporar en el archivo ejecutable.  Es posible que pueden producir en el programa llame a la función virtual equivocada.

Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para los tipos o variables.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4743. Para compilarlo, coloque ambos archivos en la misma carpeta y, a continuación, ejecutar  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
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

```cpp
// C4743b.cpp
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
