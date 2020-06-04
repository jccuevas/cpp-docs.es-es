---
title: alloc_text (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 7ddb12b39e068dea42f7a47f7fd937424be43725
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216337"
---
# <a name="alloc_text-pragma"></a>alloc_text (Pragma)

Designa la sección de código donde residirán las definiciones de función especificadas. La directiva pragma debe aparecer entre un declarador de función y la definición de función para las funciones designadas.

## <a name="syntax"></a>Sintaxis

> **#pragma alloc_text (** "*textsection*" **,** *function1* [ **,** *función2* ...] **)**

## <a name="remarks"></a>Comentarios

La Directiva pragma **alloc_text** no controla C++ funciones miembro ni funciones sobrecargadas. Solo es aplicable a las funciones declaradas con vinculación C, es decir, las funciones declaradas con la especificación de vinculación **extern "C"** . Si intenta utilizar esta directiva pragma en una función con vinculación de C++, se genera un error del compilador.

Puesto que no se `__based` admite el direccionamiento de funciones mediante, la especificación de ubicaciones de sección requiere el uso de la pragma **alloc_text** . El nombre especificado por *textsection* debe ir entre comillas dobles.

La Directiva pragma **alloc_text** debe aparecer después de las declaraciones de cualquiera de las funciones especificadas y antes de las definiciones de estas funciones.

Las funciones a las que se hace referencia en una pragma **alloc_text** deben definirse en el mismo módulo que la pragma. De lo contrario, si una función sin definir se compila posteriormente en una sección de texto diferente, puede que el error se detecte o no. Aunque lo normal es que el programa se ejecute correctamente, la función no se asignará en las secciones previstas.

Otras limitaciones de **alloc_text** son las siguientes:

- No se puede utilizar dentro de una función.

- Debe utilizarse una vez declarada la función, pero antes de que esta se haya definido.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
