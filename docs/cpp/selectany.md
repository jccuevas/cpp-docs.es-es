---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e8ca82900ffd16264aca494950d4793029e55d9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365602"
---
# <a name="selectany"></a>selectany

**Microsoft Specific**

Indica al compilador que el elemento de datos globales declarado (variable u objeto) es un COMDAT de selección (una función empaquetada).

## <a name="syntax"></a>Sintaxis

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Observaciones

En tiempo de vinculación, si se ven varias definiciones de un COMDAT, el vinculador selecciona una y descarta el resto. Si se selecciona la opción del vinculador [/OPT:REF](../build/reference/opt-optimizations.md) (Optimizaciones), se producirá la eliminación comDAT para quitar todos los elementos de datos sin referencia en la salida del vinculador.

Los constructores y la asignación mediante una función global o métodos estáticos en la declaración no crean una referencia y no impedirán la eliminación de /OPT:REF. No se debe depender de los efectos secundarios de ese código si no existen otras referencias a los datos.

Para los objetos globales inicializados dinámicamente, **selectany** descartará también el código de inicialización de un objeto sin referencia.

Un elemento de datos globales se puede inicializar normalmente solo una vez en un proyecto EXE o DLL. **selectany** se puede utilizar en la inicialización de datos globales definidos por encabezados, cuando el mismo encabezado aparece en más de un archivo de origen. **selectany** está disponible en los compiladores C y C++.

> [!NOTE]
> **selectany** solo se puede aplicar a la inicialización real de elementos de datos globales que son visibles externamente.

## <a name="example"></a>Ejemplo

Este código muestra cómo utilizar el atributo **selectany:**

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Ejemplo

Este código muestra cómo utilizar el atributo **selectany** para garantizar el plegado comDAT de datos cuando también se utiliza la opción del vinculador [/OPT:ICF.](../build/reference/opt-optimizations.md) Tenga en cuenta que los datos deben estar marcados con **selectany** y colocarse en una sección **const** (readonly). Debe especificar explícitamente la sección de solo lectura.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
