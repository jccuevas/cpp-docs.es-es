---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 264ac0a56996b0dcbeeb64246623eca1a3fc73ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172157"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

Un *puntero interior* declara un puntero al interior de un tipo de referencia, pero no al propio objeto. Un puntero interior puede apuntar a un manipulador de referencia, un tipo de valor, un manipulador de tipo al que se aplica la conversión boxing, el miembro de un tipo administrado o a un elemento de una matriz administrada.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

En el siguiente ejemplo de sintaxis se muestra un puntero interior.

### <a name="syntax"></a>Sintaxis

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>Parámetros

*cv_qualifier*<br/>
Calificadores **const** o **volatile**.

*type*<br/>
El tipo de *initializer*.

*var*<br/>
El nombre de la variable **interior_ptr**.

*initializer*<br/>
Un miembro de un tipo de referencia, elemento de una matriz administrada o cualquier otro objeto que se pueda asignar a un puntero nativo.

### <a name="remarks"></a>Observaciones

Un puntero nativo no puede hacer el seguimiento de un elemento dado que su ubicación cambia en el montón administrado, lo que da lugar a que el recolector de elementos no utilizados mueva instancias de un objeto. Para que un puntero haga referencia correctamente a la instancia, el puntero se debe actualizar en tiempo de ejecución al objeto recién posicionado.

Una variable **interior_ptr** representa un supraconjunto de la funcionalidad de un puntero nativo.  Por lo tanto, todo lo que se puede asignar a un puntero nativo también se puede asignar a una variable **interior_ptr**.  Se permite que un puntero interior realice el mismo conjunto de operaciones que los punteros nativos, incluida la comparación y la aritmética de punteros.

Un puntero interior solo se puede declarar en la pila.  No se puede declarar como miembro de una clase.

Puesto que los punteros interiores existen solo en la pila, al tomar la dirección de un puntero interior se produce un puntero no administrado.

**interior_ptr** tiene una conversión implícita a **bool**, que permite su uso en instrucciones condicionales.

Para información sobre cómo declarar un puntero interior que apunta a un objeto que no se puede mover en el montón de recolección de elementos no utilizados, consulte [pin_ptr](pin-ptr-cpp-cli.md).

**interior_ptr** está en el espacio de nombres cli.  Para más información, consulte [Espacios de nombres de plataforma, predeterminado y CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Para más información sobre los punteros interiores, consulte:

- [Procedimiento para declarar y usar punteros internos y matrices administradas (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [Procedimiento para declarar tipos de valor con la palabra clave interior_ptr (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [Procedimiento para sobrecargar funciones con punteros internos y punteros nativos (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [Procedimiento para declarar punteros internos con la palabra clave const (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se muestra cómo declarar y usar un puntero interior en un tipo de referencia.

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
