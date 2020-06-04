---
title: data_seg (Pragma)
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220384"
---
# <a name="data_seg-pragma"></a>data_seg (Pragma)

Especifica la sección de datos (segmento) donde se almacenan las variables inicializadas en el archivo de objeto (. obj).

## <a name="syntax"></a>Sintaxis

> **#pragma data_seg (** ["*nombre de sección*" [ **,** "*section-Class*"]] **)** \
> **#pragma data_seg (** { **inserte** | **pop** } [ **,** *Identifier* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Parámetros

**enviar**\
Opta Coloca un registro en la pila interna del compilador. Una **inserciones** puede tener un *identificador* y un *nombre de sección*.

**emergente**\
Opta Quita un registro de la parte superior de la pila interna del compilador. Un **pop** puede tener un *identificador* y un *nombre de sección*. Puede extraer varios registros con un solo comando **pop** mediante el *identificador*. La *sección-Name* se convierte en el nombre de la sección de datos activo después del pop.

*identificador*\
Opta Cuando se usa con la **extracción**, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quite el *identificador* . Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

*Identifier* permite extraer varios registros con un solo comando **pop** .

*"Section-name"* \
Opta Nombre de una sección. Cuando se usa con **pop**, se extrae la pila y *section-Name* se convierte en el nombre de la sección de datos activa.

*"Section-Class"* \
Opta Se omite, pero se incluye por compatibilidad con versiones C++ de Microsoft anteriores a la versión 2,0.

## <a name="remarks"></a>Comentarios

Una *sección* de un archivo objeto es un bloque de datos con nombre que se carga en la memoria como una unidad. Una *sección de datos* es una sección que contiene datos inicializados. En este artículo, los términos *segmento* y *sección* tienen el mismo significado.

La sección predeterminada del archivo. obj para las variables inicializadas es `.data`. Las variables que no se inicializan se consideran inicializadas en cero y se almacenan en `.bss`.

La Directiva pragma **data_seg** indica al compilador que Coloque todos los elementos de datos inicializados de la unidad de traducción en una sección de datos denominada *section-Name*. De forma predeterminada, la sección de datos que se usa para los datos inicializados en `.data`un archivo objeto se denomina. Las variables que no se inicializan se consideran inicializadas en cero y se almacenan en `.bss`. Una directiva pragma **data_seg** sin un parámetro *de nombre de sección* restablece el nombre de sección de datos para los elementos de datos inicializados posteriores a `.data`.

Los datos asignados mediante **data_seg** no conservan ninguna información sobre su ubicación.

Para obtener una lista de los nombres que no se deben usar para crear una sección, vea [/section](../build/reference/section-specify-section-attributes.md).

También puede especificar secciones para variables const ([const_seg](../preprocessor/const-seg.md)), datos no inicializados ([bss_seg](../preprocessor/bss-seg.md)) y funciones ([code_seg](../preprocessor/code-seg.md)).

Puede usar [dumpbin. Aplicación EXE](../build/reference/dumpbin-command-line.md) para ver los archivos de objeto. Las versiones de DUMPBIN para cada arquitectura de destino compatible se incluyen con Visual Studio.

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
