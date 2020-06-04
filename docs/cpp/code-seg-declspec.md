---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180841"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Específicos de Microsoft**

El atributo de declaración **code_seg** nombra un segmento de texto ejecutable en el archivo. obj en el que se almacenará el código objeto de las funciones miembro de la función o clase.

## <a name="syntax"></a>Sintaxis

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Observaciones

El atributo `__declspec(code_seg(...))` permite colocar código en segmentos con nombre diferentes que se pueden paginar o bloquear en memoria individualmente. Este atributo se puede usar para controlar la posición de las plantillas con instancia y del código generado por el compilador.

Un *segmento* es un bloque de datos con nombre en un archivo. obj que se carga en la memoria como una unidad. Un *segmento de texto* es un segmento que contiene código ejecutable. La *sección* term se usa a menudo indistintamente con Segment.

El código objeto que se genera cuando se define `declarator` se coloca en el segmento de texto especificado por `segname`, que es un literal de cadena de caracteres estrechos. El nombre `segname` no tiene que especificarse en una pragma [section](../preprocessor/section.md) antes de que se pueda usar en una declaración. De forma predeterminada, cuando no se especifica `code_seg`, el código objeto se coloca en un segmento denominado .text. Un atributo de **code_seg** invalida cualquier directiva de [code_seg de #pragma](../preprocessor/code-seg.md) existente. Un atributo **code_seg** aplicado a una función miembro reemplaza cualquier atributo **code_seg** aplicado a la clase envolvente.

Si una entidad tiene un atributo **code_seg** , todas las declaraciones y definiciones de la misma entidad deben tener atributos **code_seg** idénticos. Si una clase base tiene un atributo **code_seg** , las clases derivadas deben tener el mismo atributo.

Cuando se aplica un atributo **code_seg** a una función de ámbito de espacio de nombres o a una función miembro, el código objeto de esa función se coloca en el segmento de texto especificado. Cuando este atributo se aplica a una clase, todas las funciones miembro de la clase y las clases anidadas (esto incluye las funciones miembro especiales generadas por el compilador) se colocan en el segmento especificado. Las clases definidas localmente (por ejemplo, las clases definidas en el cuerpo de una función miembro) no heredan el atributo **code_seg** del ámbito de inclusión.

Cuando se aplica un atributo **code_seg** a una clase de plantilla o una función de plantilla, todas las especializaciones implícitas de la plantilla se colocan en el segmento especificado. Las especializaciones explícitas o parciales no heredan el **code_seg** atributo de la plantilla principal. Puede especificar el mismo atributo de **code_seg** o otro diferente en la especialización. No se puede aplicar un atributo **code_seg** a una creación de instancias de plantilla explícita.

De forma predeterminada, el código generado por el compilador como una función miembro especial se coloca en el segmento .text. La directiva `#pragma code_seg` no invalida este valor predeterminado. Use el atributo **code_seg** en la clase, plantilla de clase o plantilla de función para controlar dónde se coloca el código generado por el compilador.

Las lambdas heredan **code_seg** atributos de su ámbito de inclusión. Para especificar un segmento para una expresión lambda, aplique un **code_seg** atributo después de la cláusula de declaración de parámetros y antes de cualquier especificación mutable o de excepción, cualquier especificación de tipo de valor devuelto final y el cuerpo de la expresión lambda. Para obtener más información, vea [Sintaxis de expresiones lambda](../cpp/lambda-expression-syntax.md). En este ejemplo se define una expresión lambda en un segmento denominado PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Tenga cuidado cuando coloque determinadas funciones miembro, especialmente funciones miembro virtuales, en segmentos diferentes. Si se define una función virtual en una clase derivada que reside en un segmento paginado cuando el método de la clase base reside en un segmento no paginado, otros métodos de clase base o el código de usuario puede suponer que al invocar el método virtual no se desencadenará un error de página.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo un atributo **code_seg** controla la selección de ubicación de segmentos cuando se usa la especialización de plantilla implícita y explícita:

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
