---
title: Archivos de código fuente y programas de origen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50486a785530e1ba784eaede97a10fa0d300ea6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110853"
---
# <a name="source-files-and-source-programs"></a>Archivos de código fuente y programas de origen

Un programa de origen se puede dividir en uno o más "archivos de código fuente" o "unidades de traducción". La entrada del compilador se denomina "unidad de traducción".

## <a name="syntax"></a>Sintaxis

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

En [Información general de declaraciones](../c-language/overview-of-declarations.md) se proporciona la sintaxis para `declaration` no terminal, y en la *Referencia del preprocesador* se explica cómo se procesa la [unidad de traducción](../preprocessor/phases-of-translation.md).

> [!NOTE]
>  Vea la introducción a [Resumen de la sintaxis de lenguaje C](../c-language/c-language-syntax-summary.md) para obtener una explicación de las convenciones de sintaxis de ANSI.

Los componentes de una unidad de traducción son las declaraciones externas que incluyen definiciones de función y declaraciones de identificador. Estas declaraciones y definiciones pueden estar en los archivos de código fuente, archivos de encabezado, bibliotecas y otros archivos que el programa necesita. Debe compilar cada unidad de traducción y vincular los archivos objeto resultantes para crear un programa.

Un "programa de origen" de C es una colección de directivas, pragmas, declaraciones, definiciones, bloques de instrucciones y funciones. Para ser componentes válidos de un programa de Microsoft C, deben ajustarse a la sintaxis descrita en este libro, aunque pueden aparecer en cualquier orden en el programa (de conformidad con las reglas descritas en este libro). Sin embargo, la ubicación de estos componentes en un programa afecta al modo en que se pueden utilizar las variables y funciones en un programa. (Vea [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md) para obtener más información).

Los archivos de código fuente no tienen que contener instrucciones ejecutables. Por ejemplo, puede resultarle útil colocar las definiciones de variables en un archivo de código fuente y, a continuación, declarar las referencias a estas variables en otros archivos de código fuente que las usen. Esta técnica facilita la búsqueda y actualización de las definiciones cuando es necesario. Por la misma razón, las constantes y macros se organizan en archivos independientes, denominados "archivos de inclusión" o "archivos de encabezado", a los que se puede hacer referencia en archivos de código fuente según sea necesario. Vea la *Referencia del preprocesador* para obtener información sobre [macros](../preprocessor/macros-c-cpp.md) y [archivos de inclusión](../preprocessor/hash-include-directive-c-cpp.md).

## <a name="see-also"></a>Vea también

[Estructura del programa](../c-language/program-structure.md)