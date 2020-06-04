---
title: const_seg (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 845583889eb922ba97d145eefe6bca280a83817b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220434"
---
# <a name="const_seg-pragma"></a>const_seg (Pragma)

Especifica la sección (segmento) donde se almacenan las variables [const](../cpp/const-cpp.md) en el archivo objeto (. obj).

## <a name="syntax"></a>Sintaxis

> **#pragma const_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma const_seg (** { **inserte** | **pop** } [ **,** *Identifier* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Parámetros

**enviar**\
Opta Coloca un registro en la pila interna del compilador. Una **inserciones** puede tener un *identificador* y un *nombre de sección*.

**emergente**\
Opta Quita un registro de la parte superior de la pila interna del compilador. Un **pop** puede tener un *identificador* y un *nombre de sección*. Puede extraer varios registros con un solo comando **pop** mediante el *identificador*. La *sección-Name* se convierte en el nombre de la sección const activa después del pop.

*identificador*\
Opta Cuando se usa con la **extracción**, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, la Directiva extrae los registros de la pila interna hasta que se quita el *identificador* . Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

"*section-Name*" \
Opta Nombre de una sección. Cuando se usa con **pop**, se extrae la pila y *section-Name* se convierte en el nombre de sección const activo.

"*section-Class*" \
Opta Se omite, pero se incluye por compatibilidad con versiones C++ de Microsoft anteriores a la versión 2,0.

## <a name="remarks"></a>Comentarios

Una *sección* de un archivo objeto es un bloque de datos con nombre que se carga en la memoria como una unidad. Una *sección const* es una sección que contiene datos constantes. En este artículo, los términos *segmento* y *sección* tienen el mismo significado.

La Directiva pragma **const_seg** indica al compilador que Coloque todos los elementos de datos constantes de la unidad de traducción en una sección const denominada *section-Name*. La sección predeterminada en el archivo objeto para variables **const** es `.rdata`. Algunas variables **const** , como escalares, se insertan automáticamente en el flujo de código. El código insertado no aparece en `.rdata`. Una directiva pragma **const_seg** sin un parámetro *section-Name* restablece el nombre de sección de los elementos de datos **const** siguientes `.rdata`en.

Si define un objeto que requiere la inicialización dinámica en `const_seg`un, el resultado es un comportamiento indefinido.

Para obtener una lista de los nombres que no se deben usar para crear una sección, vea [/section](../build/reference/section-specify-section-attributes.md).

También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos no inicializados ([bss_seg](../preprocessor/bss-seg.md)) y funciones ([code_seg](../preprocessor/code-seg.md)).

Puede usar [dumpbin. Aplicación EXE](../build/reference/dumpbin-command-line.md) para ver los archivos de objeto. Las versiones de DUMPBIN para cada arquitectura de destino compatible se incluyen con Visual Studio.

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
