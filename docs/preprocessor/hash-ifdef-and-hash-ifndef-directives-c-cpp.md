---
title: '#ifdef e #ifndef (Directivas) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220106"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>directivas #ifdef y #ifndef (C/C++)

Las directivas **#ifdef** y **#ifndef** tienen el mismo efecto que la directiva [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) cuando se usa con el operador **definido** .

## <a name="syntax"></a>Sintaxis

> **#ifdef** *identificador* de\
> **#ifndef** *identificador* de

Estas directivas son equivalentes a:

> **#if definido** *identificador* de\
> **#if! Defined** *identificador* de

## <a name="remarks"></a>Comentarios

Puede usar las directivas **#ifdef** y **#ifndef** en cualquier `#if` lugar donde se pueda usar. La instrucción **#ifdef** *Identifier* es equivalente a `#if 1` cuando se ha definido *Identifier* . Es equivalente a `#if 0` cuando el *identificador* no se ha definido o no está definido por la `#undef` Directiva. Estas directivas solo comprueban la presencia o ausencia de identificadores definidos con `#define`, no comprueban los identificadores declarados en el código fuente de C o C++.

Estas directivas se proporcionan únicamente por compatibilidad con las versiones anteriores del lenguaje. Se prefiere la expresión constante **definida (** *Identifier* **)** utilizada con `#if` la Directiva.

La directiva **#ifndef** comprueba el contrario de la condición comprobada por **#ifdef**. Si el identificador no se ha definido, o si su definición se ha quitado con `#undef`, la condición es true (distinto de cero). De lo contrario, la condición es false (0).

**Específicos de Microsoft**

El *identificador* se puede pasar desde la línea de comandos mediante la opción [/d](../build/reference/d-preprocessor-definitions.md) . Se pueden especificar hasta 30 macros con `/D`.

La directiva **#ifdef** es útil para comprobar si existe una definición, porque una definición se puede pasar desde la línea de comandos. Por ejemplo:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
