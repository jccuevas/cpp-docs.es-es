---
title: bss_seg (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: a343fb45b4bbe4789f38b7a1102572cf4241ec53
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218548"
---
# <a name="bss_seg-pragma"></a>bss_seg (Pragma)

Especifica la sección (segmento) en la que se almacenan las variables sin inicializar en el archivo objeto (. obj).

## <a name="syntax"></a>Sintaxis

> **#pragma bss_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma bss_seg (** { **inserte** | **pop** } [ **,** *Identifier* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Parámetros

**enviar**\
Opta Coloca un registro en la pila interna del compilador. Una **inserciones** puede tener un *identificador* y un *nombre de sección*.

**emergente**\
Opta Quita un registro de la parte superior de la pila interna del compilador. Un **pop** puede tener un *identificador* y un *nombre de sección*. Puede extraer varios registros con un solo comando **pop** mediante el *identificador*. La *sección-Name* se convierte en el nombre de la sección de BSS activa después del pop.

*identificador*\
Opta Cuando se usa con la **extracción**, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, la Directiva extrae los registros de la pila interna hasta que se quita el *identificador* . Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

*"Section-name"* \
Opta Nombre de una sección. Cuando se usa con **pop**, se extrae la pila y *section-Name* se convierte en el nombre de la sección de BSS activa.

*"Section-Class"* \
Opta Se omite, pero se incluye por compatibilidad con versiones C++ de Microsoft anteriores a la versión 2,0.

## <a name="remarks"></a>Comentarios

Una *sección* de un archivo objeto es un bloque de datos con nombre que se carga en la memoria como una unidad. Una *sección de BSS* es una sección que contiene datos no inicializados. En este artículo, los términos *segmento* y *sección* tienen el mismo significado.

La Directiva pragma **bss_seg** indica al compilador que Coloque todos los elementos de datos no inicializados de la unidad de traducción en una sección de BSS denominada *section-Name*. En algunos casos, el uso de **bss_seg** puede acelerar los tiempos de carga agrupando los datos no inicializados en una sección. De forma predeterminada, la sección de BSS utilizada para los datos no inicializados en un archivo `.bss`objeto se denomina. Una directiva pragma **bss_seg** sin un parámetro *section-Name* restablece el nombre de la sección de BSS para los elementos de datos no inicializados subsiguientes en `.bss`.

Los datos asignados mediante la pragma **bss_seg** no conservan ninguna información sobre su ubicación.

Para obtener una lista de los nombres que no se deben usar para crear una sección, vea [/section](../build/reference/section-specify-section-attributes.md).

También puede especificar secciones para los datos inicializados ([data_seg](../preprocessor/data-seg.md)), las funciones ([code_seg](../preprocessor/code-seg.md)) y las variables const ([const_seg](../preprocessor/const-seg.md)).

Puede usar [dumpbin. Aplicación EXE](../build/reference/dumpbin-command-line.md) para ver los archivos de objeto. Las versiones de DUMPBIN para cada arquitectura de destino compatible se incluyen con Visual Studio.

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
