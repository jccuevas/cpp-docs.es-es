---
title: Programa y vinculación (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4154f0951b46b1c8badc0224845d2881cc8ad573
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="program-and-linkage--c"></a>Programa y vinculación (C++)

En un programa de C++, cada símbolo global puede definirse una sola vez, incluso si el programa está formada por varias unidades de traducción. Una unidad de traducción está formada por un archivo de implementación (.cpp, .hpp, .cxx, etcetera) y todos los encabezados que incluye directa o indirectamente. Un programa consta de una o más unidades de traducción vinculadas entre sí. 

## <a name="linkage-vs-scope"></a>Vinculación frente a ámbito

El concepto de *vinculación* hace referencia a la visibilidad de símbolos globales (por ejemplo, las variables, los nombres de tipo y los nombres de función) dentro del programa como un todo a través de unidades de traducción. El concepto de *ámbito* hace referencia a los símbolos que se declaran dentro de un bloque, como un espacio de nombres, la clase o el cuerpo de la función. Estos símbolos solo son visibles dentro del ámbito en el que se definen; el concepto de vinculación no se aplica a ellos.

## <a name="external-vs-internal-linkage"></a>Externa frente a la vinculación interna

Variables globales no son constantes y funciones libres de forma predeterminada tienen vinculación externa; son visibles desde cualquier unidad de traducción en el programa. Puede invalidar este comportamiento al declararlas como de forma explícita **estático** lo que limita su visibilidad en la misma unidad de traducción en el que se declaran. Este significado del **estático** es diferente de su significado cuando se aplica a las variables locales. Las variables declaradas como **const** tienen vinculación interna de forma predeterminada.

## <a name="extern-constexpr-linkage"></a>Vinculación de extern constexpr

En versiones anteriores de Visual Studio, el compilador siempre le asignó una vinculación interna de constexpr variable aunque la variable se ha marcado como extern. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador (/Zc:externConstexpr) permite un comportamiento correcto que cumple con los estándares. Este acabará convirtiéndose en el conmutador predeterminado.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene un constexpr variable extern declarado, deba marcarse **__declspec (selectany)** para tener correctamente sus declaraciones duplicadas combinadas:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>Vea también

 [Conceptos básicos](../cpp/basic-concepts-cpp.md)