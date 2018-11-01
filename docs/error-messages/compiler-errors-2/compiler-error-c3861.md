---
title: Error del compilador C3861
ms.date: 03/23/2018
f1_keywords:
- C3861
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
ms.openlocfilehash: 4ebfd3b0129e25cf543cac803a3b33fb074f3d70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530811"
---
# <a name="compiler-error-c3861"></a>Error del compilador C3861

> '*identificador*': no se encontró el identificador

El compilador no pudo resolver una referencia a un identificador, incluso con una búsqueda dependiente de argumentos.

## <a name="remarks"></a>Comentarios

Para corregir este error, compare el uso de *identificador* a la declaración del identificador de caso y la ortografía. Compruebe que [operadores de resolución de ámbito](../../cpp/scope-resolution-operator.md) y espacio de nombres [directivas using](../../cpp/namespaces-cpp.md#using_directives) se usan correctamente. Si el identificador se declara en un archivo de encabezado, compruebe que se incluirá el encabezado antes de que se hace referencia el identificador. Si el identificador se ha diseñado para ser visibles externamente, asegúrese de que se declara en cualquier archivo de origen que lo utiliza. Compruebe también que la definición o declaración de identificador no se ha excluido por [directivas de compilación condicional](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Los cambios para quitar funciones obsoletas de la biblioteca en tiempo de ejecución de C en Visual Studio 2015 pueden provocar C3861. Para resolver este error, quite las referencias a estas funciones o reemplazarlos con sus alternativas seguras, si existe. Para obtener más información, consulte [funciones obsoletas](../../c-runtime-library/obsolete-functions.md).

Si aparece el error C3861 después de la migración de proyectos desde versiones anteriores del compilador, puede tener problemas relacionados con las versiones compatibles de Windows. Visual C++ ya no admite como destino Windows 95, Windows 98, Windows ME, Windows NT o Windows 2000. Si las macros **WINVER** o **_WIN32_WINNT** están asignadas a una de estas versiones de Windows, debe modificar las macros. Para obtener más información, consulte [Modificar WINVER y _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

## <a name="examples"></a>Ejemplos

### <a name="undefined-identifier"></a>Identificador no definido

El ejemplo siguiente genera C3861 porque el identificador no está definido.

```cpp
// C3861.cpp
void f2(){}
int main() {
   f();    // C3861
   f2();   // OK
}
```

### <a name="identifier-not-in-scope"></a>Identificador fuera del ámbito

El ejemplo siguiente genera C3861 porque un identificador solo está visible en el ámbito de archivo de su definición, a menos que se declara en otros archivos de origen que lo usan.

```cpp
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {
   std::cout << f() << std::endl;    // C3861
}
```

```cpp
// C3861_a2.cpp
int f() {  // declared and defined here
   return 42;
}
```

### <a name="namespace-qualification-required"></a>Calificación Namespace necesario

Las clases de excepción en la biblioteca estándar de C++ requieren el `std` espacio de nombres.

```cpp
// C3861_b.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   try {
      throw exception("Exception");   // C3861
      // try the following line instead
      // throw std::exception("Exception");
   }
   catch (...) {
      std::cout << "caught an exception" << std::endl;
   }
}
```

### <a name="obsolete-function-called"></a>Función obsoleta llamado

Funciones obsoletas se quitaron de la biblioteca CRT.

```cpp
// C3861_c.cpp
#include <stdio.h>
int main() {
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C3861
   // Use gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

### <a name="adl-and-friend-functions"></a>Funciones ADL y friend

El ejemplo siguiente genera C3767 porque el compilador no puede usar la búsqueda dependiente de argumentos para `FriendFunc`:

```cpp
namespace N {
   class C {
      friend void FriendFunc() {}
      friend void AnotherFriendFunc(C* c) {}
   };
}

int main() {
   using namespace N;
   FriendFunc();   // C3861 error
   C* pC = new C();
   AnotherFriendFunc(pC);   // found via argument-dependent lookup
}
```

Para corregir el error, declare la función friend en el ámbito de clase y definirla en el ámbito de espacio de nombres:

```cpp
class MyClass {
   int m_private;
   friend void func();
};

void func() {
   MyClass s;
   s.m_private = 0;
}

int main() {
   func();
}
```
