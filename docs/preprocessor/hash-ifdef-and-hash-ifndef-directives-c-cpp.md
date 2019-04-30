---
title: '#ifdef e #ifndef (directivas) (C/C ++)'
ms.date: 11/04/2016
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
ms.openlocfilehash: d7a6a1604df03f0607f33e42880270cbdcd62e8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409881"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef e #ifndef (Directivas) (C/C++)
El **#ifdef** y **#ifndef** directivas realizan la misma tarea que el `#if` directiva cuando se usa con **definido**( *identificador* ).

## <a name="syntax"></a>Sintaxis

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>Comentarios

Puede usar el **#ifdef** y **#ifndef** directivas en cualquier lugar `#if` se puede usar. El **#ifdef** *identificador* es equivalente a la instrucción `#if 1` cuando *identificador* se ha definido, y es equivalente a `#if 0` cuando *identificador* no se ha definido o no se ha definido con el `#undef` directiva. Estas directivas solo comprueban la presencia o ausencia de identificadores definidos con `#define`, no comprueban los identificadores declarados en el código fuente de C o C++.

Estas directivas se proporcionan únicamente por compatibilidad con las versiones anteriores del lenguaje. El **definido (** *identificador* **)** expresión constante que se utiliza con el `#if` se prefiere la directiva.

El **#ifndef** directiva comprueba el opuesto de la condición que comprueba **#ifdef**. Si el identificador no se ha definido (o su definición se ha quitado con `#undef`), la condición es true (distinto de cero). De lo contrario, la condición es false (0).

**Específicos de Microsoft**

El *identificador* se puede pasar desde la línea de comandos mediante el `/D` opción. Se pueden especificar hasta 30 macros con `/D`.

Es útil para comprobar si existe una definición, porque una definición se puede pasar desde la línea de comandos. Por ejemplo:

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