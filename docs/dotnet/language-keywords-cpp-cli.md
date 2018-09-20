---
title: Palabras clave del lenguaje (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b9deb25e203ea805b1430b2ec8e56f17a50123b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445443"
---
# <a name="language-keywords-ccli"></a>Palabras clave del lenguaje (C++/CLI)

Varias palabras clave del lenguaje cambiadas de extensiones administradas para C++ a Visual C++.

En la nueva sintaxis de Visual C++, se quita el carácter de subrayado doble como prefijo de todas las palabras clave (con una excepción: `__identifier` se conservan). Por ejemplo, una propiedad ahora está declarada como `property`, no `__property`.

Había dos razones principales para utilizar el prefijo con subrayado doble en extensiones administradas:

- Es el método compatible de proporcionar extensiones locales al estándar ISO C++. Un objetivo principal del diseño de extensiones administradas era no presentan incompatibilidades con el lenguaje estándar, como las nuevas palabras clave y tokens. Fue este motivo, en gran medida, lo que motivó la elección de la sintaxis de puntero de la declaración de objetos de tipos de referencia administrada.

- El uso del subrayado doble, aparte de su aspecto compatible, también es una garantía razonable de no ser invasivo con la base de código existente de los usuarios del lenguaje. Esto fue un segundo objetivo principal del diseño de extensiones administradas.

A pesar de quitar los caracteres de subrayado dobles, Microsoft sigue comprometido a ser compatibles. Sin embargo, compatibilidad con el modelo de objeto dinámico de CLR representa un paradigma de programación de nuevo y eficaces. Compatibilidad con este nuevo paradigma requiere sus propias palabras clave de alto nivel y los tokens. Siempre hemos querido proporcionar una expresión de primera clase de este nuevo paradigma mientras lo integramos y que admiten el lenguaje estándar. El nuevo diseño de sintaxis proporciona una experiencia de programación de primera clase de estos dos modelos de objetos dispares.

De forma similar, estamos interesados en maximizar la naturaleza no invasiva de estas palabras clave del lenguaje nuevo. Esto se ha logrado con el uso de palabras clave contextuales y espaciadas. Antes de adentrarnos en la nueva sintaxis del lenguaje real, vamos a intentar dar sentido a estos dos modos de palabra clave especial.

Una palabra clave contextual tiene un significado especial dentro de los contextos de programa específico. En el programa general, por ejemplo, `sealed` se trata como un identificador normal. Sin embargo, cuando se produce dentro de la parte de la declaración de un tipo de clase de referencia administrada, se trata como palabra clave en el contexto de esa declaración de clase. Esto minimiza el posible impacto invasivo de introducir una nueva palabra clave en el lenguaje, algo que creemos que es muy importante para los usuarios con un código base existente. Al mismo tiempo, permite a los usuarios de la nueva funcionalidad tener una experiencia de primera clase de la característica de idioma adicionales: algo que no era posible con extensiones administradas. Para obtener un ejemplo de cómo `sealed` sirve vea [declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md).

Una palabra clave espaciada, tales como `value class`, es un caso especial de una palabra clave contextual. Empareja una palabra clave existente con un modificador contextual separado por un espacio. El par se trata como una sola unidad en lugar de dos palabras clave independientes.

## <a name="see-also"></a>Vea también

[Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)