---
title: code_seg (__declspec) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae69cd9e88b97a31dda86648d86e143ab9bd5d40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)
**Específicos de Microsoft**  
  
 El atributo de declaración `code_seg` asigna nombre a un segmento de texto ejecutable del archivo .obj en el que se almacenará el código objeto para la función o las funciones miembro de clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(code_seg("segname")) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo `__declspec(code_seg(...))` permite colocar código en segmentos con nombre diferentes que se pueden paginar o bloquear en memoria individualmente. Este atributo se puede usar para controlar la posición de las plantillas con instancia y del código generado por el compilador.  
  
 A *segmento* es un bloque de datos en un archivo .obj que se carga en memoria como una unidad con nombre. A *segmento de texto* es un segmento que contiene código ejecutable. El término *sección* se suelen utilizar indistintamente con el segmento.  
  
 El código objeto que se genera cuando se define `declarator` se coloca en el segmento de texto especificado por `segname`, que es un literal de cadena de caracteres estrechos. El nombre `segname` no tiene que especificarse en un [sección](../preprocessor/section.md) pragma antes de que se puede utilizar en una declaración. De forma predeterminada, cuando no se especifica `code_seg`, el código objeto se coloca en un segmento denominado .text. A `code_seg` atributo invalida cualquier existente [#pragma code_seg](../preprocessor/code-seg.md) directiva. Un atributo `code_seg` aplicado a una función miembro invalida cualquier atributo `code_seg` aplicado a la clase envolvente.  
  
 Si una entidad tiene un atributo `code_seg`, todas las declaraciones y definiciones de la misma entidad deben tener atributos `code_seg` idénticos. Si una clase base tiene un atributo `code_seg`, las clases derivadas deben tener el mismo atributo.  
  
 Cuando se aplica un atributo `code_seg` a una función o una función miembro que tiene ámbito de espacio de nombres, el código objeto de esa función se coloca en el segmento de texto especificado. Cuando este atributo se aplica a una clase, todas las funciones miembro de la clase y las clases anidadas (esto incluye las funciones miembro especiales generadas por el compilador) se colocan en el segmento especificado. Las clases definidas localmente (por ejemplo, las clases definidas en el cuerpo de una función miembro) no heredan el atributo `code_seg` del ámbito de inclusión.  
  
 Cuando se aplica un atributo `code_seg` a una clase de plantilla o una función de plantilla, todas las especializaciones implícitas de la plantilla se colocan en el segmento especificado. Las especializaciones explícitas o parciales no heredan el atributo `code_seg` de la plantilla principal. Se puede especificar el mismo atributo `code_seg` u otro diferente en la especialización. No se puede aplicar un atributo `code_seg` a una creación de instancias explícitas de plantilla.  
  
 De forma predeterminada, el código generado por el compilador como una función miembro especial se coloca en el segmento .text. La directiva `#pragma code_seg` no invalida este valor predeterminado. El atributo `code_seg` se usa en la clase, la plantilla de clase o la plantilla de función para controlar dónde se coloca el código generado por el compilador.  
  
 Las lambdas heredan los atributos `code_seg` de su ámbito de inclusión. Para especificar un segmento para una expresión lambda, se aplica un atributo `code_seg` después de la cláusula de declaración de parámetros y antes de cualquier especificación mutable o de excepciones, cualquier especificación de tipo de valor devuelto final y el cuerpo de la expresión lambda. Para obtener más información, consulte [sintaxis de expresiones Lambda](../cpp/lambda-expression-syntax.md). En este ejemplo se define una expresión lambda en un segmento denominado PagedMem:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Tenga cuidado cuando coloque determinadas funciones miembro, especialmente funciones miembro virtuales, en segmentos diferentes. Si se define una función virtual en una clase derivada que reside en un segmento paginado cuando el método de la clase base reside en un segmento no paginado, otros métodos de clase base o el código de usuario puede suponer que al invocar el método virtual no se desencadenará un error de página.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo un atributo `code_seg` controla la posición de un segmento cuando se usa la especialización de plantilla implícita y explícita:  
  
```  
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
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)