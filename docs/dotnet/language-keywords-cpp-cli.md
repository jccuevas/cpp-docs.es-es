---
title: Palabras clave del lenguaje (C++ / CLI) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e1107ad45feaae470ed2a7481f80bb17c389042d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="language-keywords-ccli"></a>Palabras clave del lenguaje (C++/CLI)
Varias palabras clave del lenguaje ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En la nueva sintaxis de Visual C++, se quita el subrayado doble como prefijo de todas las palabras clave (con una excepción: `__identifier` se conserva). Por ejemplo, ahora se declara una propiedad como `property`, no `__property`.  
  
 Hay dos razones principales para utilizar el prefijo de subrayado doble en extensiones administradas:  
  
-   Es el método compatible de proporcionar extensiones locales a la norma ISO C++. Un objetivo principal del diseño de extensiones administradas era no introducir incompatibilidades con el lenguaje estándar, como nuevas palabras clave y símbolos (tokens). Fue esta razón, en gran medida, lo que motivó la elección de la sintaxis de puntero para la declaración de objetos de tipos de referencia administrada.  
  
-   El uso del subrayado doble, aparte de su aspecto compatible, también es una garantía razonable de no ser invasivo con la base de código existente de los usuarios del lenguaje. Esto era un segundo objetivo principal del diseño de extensiones administradas.  
  
 A pesar de quitar los caracteres de subrayado dobles, Microsoft mantiene su compromiso por ser compatibles. Sin embargo, compatibles con el modelo de objeto dinámico de CLR representa un paradigma de programación de nuevo y eficaz. Compatibilidad con este nuevo paradigma requiere sus propias palabras clave de alto nivel y símbolos (tokens). Hemos intentado proporcionar una expresión de primera clase de este nuevo paradigma mientras lo integramos y admitimos el lenguaje estándar. El nuevo diseño de sintaxis proporciona una experiencia de programación de primera clase de estos dos modelos de objetos dispares.  
  
 De igual forma, estamos interesados en maximizar la naturaleza no invasiva de estas nuevas palabras clave del lenguaje. Esto se ha logrado con el uso de palabras clave contextuales y espaciadas. Antes de adentrarnos en la nueva sintaxis del lenguaje real, vamos a intentar dar sentido a estos dos tipos de palabra clave especial.  
  
 Una palabra clave contextual tiene un significado especial dentro de los contextos de programa específico. Dentro del programa general, por ejemplo, `sealed` se trata como un identificador normal. Sin embargo, cuando se produce dentro de la parte de la declaración de un tipo de clase de referencia administrada, se trata como una palabra clave en el contexto de esa declaración de clase. Esto reduce el posible impacto invasivo de introducir una nueva palabra clave en el lenguaje, algo que creemos que es muy importante para los usuarios con una base de código existente. Al mismo tiempo, permite que los usuarios de la nueva funcionalidad tener una experiencia de primera clase de la característica de idioma adicional - algo que no era posible con extensiones administradas. Para obtener un ejemplo de cómo `sealed` se utiliza vea [declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md).  
  
 Una palabra clave espaciada, como `value class`, es un caso especial de una palabra clave contextual. Empareja una palabra clave existente con un modificador contextual separado por un espacio. El par se trata como una sola unidad, en lugar de como dos palabras clave independientes.  
  
## <a name="see-also"></a>Vea también  
 [C++ / CLI manual de migraciones](../dotnet/cpp-cli-migration-primer.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)