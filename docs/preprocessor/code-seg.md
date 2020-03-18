---
title: code_seg (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 65d702273593dc7fba68cc040f700b01a2c5e4a7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446478"
---
# <a name="code_seg-pragma"></a>code_seg (pragma)

Especifica la sección de texto (segmento) en la que se almacenan las funciones en el archivo de objeto (. obj).

## <a name="syntax"></a>Sintaxis

> **#pragma code_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma code_seg (** { **inserte** | **pop** } [ **,** *Identifier* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Parámetros

\ de **extracción**
Opta Coloca un registro en la pila interna del compilador. Una **inserciones** puede tener un *identificador* y un *nombre de sección*.

\ **pop**
Opta Quita un registro de la parte superior de la pila interna del compilador. Un **pop** puede tener un *identificador* y un *nombre de sección*. Puede extraer varios registros con un solo comando **pop** mediante el *identificador*. La *sección-Name* se convierte en el nombre de la sección de texto activo después del pop.

*identificador*\
Opta Cuando se usa con la **extracción**, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, la Directiva extrae los registros de la pila interna hasta que se quita el *identificador* . Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

"*section-Name*" \
Opta Nombre de una sección. Cuando se usa con **pop**, se extrae la pila y *section-Name* se convierte en el nombre de la sección de texto activo.

"*section-Class*" \
Opta Se omite, pero se incluye por compatibilidad con versiones C++ de Microsoft anteriores a la versión 2,0.

## <a name="remarks"></a>Observaciones

Una *sección* de un archivo objeto es un bloque de datos con nombre que se carga en la memoria como una unidad. Una *sección de texto* es una sección que contiene código ejecutable. En este artículo, los términos *segmento* y *sección* tienen el mismo significado.

La Directiva pragma **code_seg** indica al compilador que coloque todo el código objeto posterior de la unidad de traducción en una sección de texto denominada *section-Name*. De forma predeterminada, la sección de texto que se usa para las funciones de un archivo objeto se denomina `.text`. Una directiva pragma **code_seg** sin un parámetro *de nombre de sección* restablece el nombre de la sección de texto del código objeto subsiguiente a `.text`.

La Directiva pragma **code_seg** no controla la colocación del código objeto generado para las plantillas con instancias. Tampoco controla el código generado implícitamente por el compilador, como funciones miembro especiales. Para controlar ese código, se recomienda utilizar en su lugar el atributo [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) . Proporciona control sobre la selección de ubicación de todo el código objeto, incluido el código generado por el compilador.

Para obtener una lista de los nombres que no se deben usar para crear una sección, vea [/section](../build/reference/section-specify-section-attributes.md).

También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos no inicializados ([bss_seg](../preprocessor/bss-seg.md)) y variables const ([const_seg](../preprocessor/const-seg.md)).

Puede usar [dumpbin. Aplicación EXE](../build/reference/dumpbin-command-line.md) para ver los archivos de objeto. Las versiones de DUMPBIN para cada arquitectura de destino compatible se incluyen con Visual Studio.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo usar la Directiva pragma **code_seg** para controlar dónde se coloca el código de objeto:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>Consulte también

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
