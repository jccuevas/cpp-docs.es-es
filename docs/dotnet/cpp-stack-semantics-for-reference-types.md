---
title: Semántica de pila de C++ para los tipos de referencia
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 4d9aaa493eab39199ac75b6b9fe888c3e103f115
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448072"
---
# <a name="c-stack-semantics-for-reference-types"></a>Semántica de pila de C++ para los tipos de referencia

Antes de Visual Studio 2005, una instancia de un tipo de referencia solo se creara con la `new` operador, que se creó el objeto en la basura recopilados de montón. Sin embargo, ahora puede crear una instancia de un tipo de referencia con la misma sintaxis que usaría para crear una instancia de un tipo nativo en la pila. Por lo tanto, no es necesario usar [ref new, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) para crear un objeto de un tipo de referencia. Y cuando el objeto queda fuera del ámbito, el compilador llama al destructor del objeto.

## <a name="remarks"></a>Comentarios

Cuando se crea una instancia de un tipo de referencia mediante la semántica de pila, el compilador internamente crea la instancia en el montón de elementos no utilizados (mediante `gcnew`).

Cuando la firma o tipo de devolución de una función incluye una instancia de un tipo de referencia por valor, la función se marcarán en los metadatos como que requiere un tratamiento especial (con modreq). Este tratamiento especial es actualmente sólo proporcionada por los clientes de Visual C++; otros lenguajes no admiten actualmente consumo de funciones o datos que usan los tipos de referencia creados con semántica de pila.

Una razón para utilizar `gcnew` (asignación dinámica) en lugar de pila semántica sería si el tipo no tiene ningún destructor. Además, el uso de los tipos de referencia creados con semántica de pila en las firmas de función no sería posible si desea que las funciones que será consumido por lenguajes distintos de Visual C++.

El compilador no generará un constructor de copias para un tipo de referencia. Por lo tanto, si define una función que usa un tipo de referencia por valor en la firma, debe definir un constructor de copias para el tipo de referencia. Un constructor de copias para un tipo de referencia tiene una firma de la forma siguiente: `R(R%){}`.

El compilador no generará un operador de asignación predeterminado para un tipo de referencia. Un operador de asignación permite crear un objeto mediante la semántica de pila y se inicializa con un objeto existente que se creó utilizando la semántica de pila. Un operador de asignación para un tipo de referencia tiene una firma de la forma siguiente: `void operator=( R% ){}`.

Si el destructor de su tipo libera los recursos críticos y usa semántica de pila para tipos de referencia, no es necesario llamar explícitamente al destructor (o llamar a `delete`). Para obtener más información sobre los destructores en tipos de referencia, consulte [destructores y finalizadores en cómo: Definir y utilizar clases y structs (C++ / c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Un operador de asignación generados por el compilador seguirá las reglas habituales de C++ estándares con las siguientes adiciones:

- Los datos no estáticos miembros cuyo tipo es un identificador para un tipo de referencia será superficial copiados (que se trata como un miembro de datos no estáticos cuyo tipo es un puntero).

- Copia de cualquier miembro de datos no estáticos cuyo tipo es que un tipo de valor será superficial.

- Cualquier miembro de datos no estáticos cuyo tipo es una instancia de un tipo de referencia invocará una llamada al constructor de copia del tipo de referencia.

El compilador también proporciona un `%` operador unario para convertir una instancia de un tipo de referencia que se creó utilizando la semántica de pila en su tipo de identificador subyacente.

Los siguientes tipos de referencia no están disponibles para su uso con semántica de pila:

- [delegate (Extensiones de componentes de C++)](../extensions/delegate-cpp-component-extensions.md)

- [Matrices](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Ejemplo de código siguiente muestra cómo declarar instancias de tipos de referencia con la semántica de pila, cómo el operador de asignación y los trabajos de constructor de copia y cómo inicializar una referencia de seguimiento con el tipo de referencia que se creó utilizando la semántica de pila.

### <a name="code"></a>Código

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Salida

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Vea también

[Clases y structs](../extensions/classes-and-structs-cpp-component-extensions.md)
