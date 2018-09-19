---
title: code_seg (__declspec) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf387283aa0d4cdb282760c4ee170a0205172d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068824"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Específicos de Microsoft**

El **code_seg** nombres de atributo de declaración de un segmento de texto ejecutable en el archivo .obj en el que se almacenará el código objeto de la función o funciones miembro de clase.

## <a name="syntax"></a>Sintaxis

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Comentarios

El atributo `__declspec(code_seg(...))` permite colocar código en segmentos con nombre diferentes que se pueden paginar o bloquear en memoria individualmente. Este atributo se puede usar para controlar la posición de las plantillas con instancia y del código generado por el compilador.

Un *segmento* es un bloque con nombre de los datos en un archivo .obj que se carga en memoria como una unidad. Un *segmento de texto* es un segmento que contiene código ejecutable. El término *sección* se suelen utilizar indistintamente con el segmento.

El código objeto que se genera cuando se define `declarator` se coloca en el segmento de texto especificado por `segname`, que es un literal de cadena de caracteres estrechos. El nombre `segname` no tiene que especificarse en un [sección](../preprocessor/section.md) pragma antes de que se puede usar en una declaración. De forma predeterminada, cuando no se especifica `code_seg`, el código objeto se coloca en un segmento denominado .text. Un **code_seg** atributo invalida cualquier existente [#pragma code_seg](../preprocessor/code-seg.md) directiva. Un **code_seg** atributo aplicado a una función miembro invalida cualquier **code_seg** atributo aplicado a la clase envolvente.

Si una entidad tiene un **code_seg** atributo, todas las declaraciones y definiciones de la misma entidad deben tener idénticos **code_seg** atributos. Si una clase base tiene un **code_seg** atributo derivado las clases deben tener el mismo atributo.

Cuando un **code_seg** atributo se aplica a una función de ámbito de espacio de nombres o una función miembro, el código objeto de esa función se coloca en el segmento de texto especificado. Cuando este atributo se aplica a una clase, todas las funciones miembro de la clase y las clases anidadas (esto incluye las funciones miembro especiales generadas por el compilador) se colocan en el segmento especificado. Las clases definidas localmente, por ejemplo, las clases definidas en el cuerpo de una función miembro, no heredan el **code_seg** atributo del ámbito de inclusión.

Cuando un **code_seg** atributo se aplica a una clase de plantilla o una función de plantilla, todas las especializaciones implícitas de la plantilla se colocan en el segmento especificado. Las especializaciones explícitas o parciales no heredan el **code_seg** atributo desde la plantilla principal. Puede especificar el mismo o a otro **code_seg** atributo en la especialización. Un **code_seg** atributo no puede aplicarse a una instancia de plantilla explícitos.

De forma predeterminada, el código generado por el compilador como una función miembro especial se coloca en el segmento .text. La directiva `#pragma code_seg` no invalida este valor predeterminado. Use la **code_seg** atributo en la clase, una plantilla de clase o una plantilla de función para controlar dónde se coloca el código generado por el compilador.

Las lambdas heredan **code_seg** los atributos de su ámbito de inclusión. Para especificar un segmento de una expresión lambda, aplique un **code_seg** atributo después de la cláusula de declaración de parámetros y antes de cualquier mutable o especificación de excepción, cualquier especificación de tipo de valor devuelto final y el cuerpo de la expresión lambda. Para obtener más información, consulte [sintaxis de expresión Lambda](../cpp/lambda-expression-syntax.md). En este ejemplo se define una expresión lambda en un segmento denominado PagedMem:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Tenga cuidado cuando coloque determinadas funciones miembro, especialmente funciones miembro virtuales, en segmentos diferentes. Si se define una función virtual en una clase derivada que reside en un segmento paginado cuando el método de la clase base reside en un segmento no paginado, otros métodos de clase base o el código de usuario puede suponer que al invocar el método virtual no se desencadenará un error de página.

## <a name="example"></a>Ejemplo

Este ejemplo se muestra cómo un **code_seg** atributo controla posición cuando implícita de un segmento y se usa la especialización de plantilla explícitos:

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

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)