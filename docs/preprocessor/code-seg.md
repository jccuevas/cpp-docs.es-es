---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: e566fb01bf70b343b75254a10466bdda2bc7ce1b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041246"
---
# <a name="codeseg"></a>code_seg
Especifica el segmento de texto donde se almacenan las funciones en el archivo .obj.

## <a name="syntax"></a>Sintaxis

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parámetros

**push**<br/>
(Opcional) Inserta un registro en la pila interna del compilador. Un **inserción** puede tener un *identificador* y *nombre de segmento*.

**pop**<br/>
(Opcional) Quita un registro de la parte superior de la pila interna del compilador.

*identifier*<br/>
(Opcional) Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta *identificador* se quita; si *identificador* no se encuentra en la pila interna, no se extrae nada.

*identificador* permite varios registros con un solo sacar **pop** comando.

"*segment-name*"<br/>
(Opcional) El nombre de un segmento. Cuando se usa con **pop**, se extrae la pila y *nombre de segmento* se convierte en el nombre del segmento de texto activo.

"*segment-class*"<br/>
(Opcional) Se omite, pero se incluye por compatibilidad con versiones anteriores a la versión 2.0 de C++.

## <a name="remarks"></a>Comentarios

El **code_seg** directiva pragma no controla la posición del código objeto generado para las plantillas con instancias ni el código generado implícitamente por el compilador, por ejemplo, las funciones miembro especiales. Se recomienda que use el [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) atributo en su lugar, ya que proporciona control sobre la posición de todo el código objeto. Esto incluye el código generado por el compilador.

Un *segmento* en un .obj archivo es un bloque de datos que se cargan en memoria como una unidad con nombre. Un *segmento de texto* es un segmento que contiene código ejecutable. En este artículo, los términos *segmento* y *sección* se usan indistintamente.

El **code_seg** directiva pragma indica al compilador que coloque todo el código objeto posterior de la unidad de traducción en un segmento de texto denominado *nombre de segmento*. De forma predeterminada, el segmento de texto usado para las funciones de un archivo .obj se denomina .text.

Un **code_seg** directiva pragma sin parámetros restablece el nombre del segmento de texto para el código objeto posterior a Text.

Puede usar el [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) aplicación para ver los archivos .obj. Las versiones de DUMPBIN para cada arquitectura de destino admitida se incluyen con Visual Studio.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo usar el **code_seg** directiva pragma para controlar dónde se coloca el código de objeto:

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

Para obtener una lista de nombres que no debe usarse para crear una sección, vea [/SECTION](../build/reference/section-specify-section-attributes.md).

También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos sin inicializar ([bss_seg](../preprocessor/bss-seg.md)) y las variables const ([const_seg](../preprocessor/const-seg.md)).

## <a name="see-also"></a>Vea también

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)