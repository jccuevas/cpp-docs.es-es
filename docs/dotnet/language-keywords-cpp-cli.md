---
title: "Palabras clave del lenguaje (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palabras clave [C++]"
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Palabras clave del lenguaje (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Han cambiado varias palabras clave del lenguaje de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En la nueva sintaxis de [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], se ha quitado el subrayado doble como prefijo de todas las palabras clave \(con una excepción: `__identifier` se conserva\).  Por ejemplo, una propiedad se declara ahora como `property` y no `__property`.  
  
 Había dos razones principales para utilizar el prefijo de subrayado doble en Extensiones administradas:  
  
-   Es el método compatible de proporcionar extensiones locales al estándar ISO C\+\+.  Un objetivo principal del diseño de Extensiones administradas era el de no introducir incompatibilidades con el lenguaje estándar, como palabras clave y símbolos \(token\) nuevos.  Fue esta razón, principalmente, la que motivó la elección de una sintaxis de puntero para la declaración de objetos de tipos de referencia administrados.  
  
-   El uso del subrayado doble, al margen de su aspecto compatible, supone igualmente una garantía razonable de no ser invasivo con la base de código existente de los usuarios del lenguaje.  Éste fue el segundo objetivo principal del diseño de Extensiones administradas.  
  
 A pesar de haber quitado los subrayado dobles, Microsoft mantiene su compromiso de compatibilidad.  Sin embargo, la compatibilidad con el modelo de objeto dinámico de CLR representa un nuevo y eficaz paradigma de programación.  La compatibilidad con este nuevo paradigma requiere sus propias palabras clave y símbolos \(token\) de alto nivel.  Hemos intentado proporcionar una expresión de primera clase de este nuevo paradigma mientras lo integramos y admitimos el lenguaje estándar.  El nuevo diseño de la sintaxis proporciona una experiencia de programación de gran calidad de estos dos modelos de objetos dispares.  
  
 De igual forma, estamos interesados en maximizar la naturaleza no invasiva de estas nuevas palabras claves del lenguaje.  Esto se ha logrado con el uso de palabras clave contextuales y espaciadas.  Antes de examinar la nueva sintaxis del lenguaje real, vamos a intentar dar sentido a estos dos tipos de palabra clave especiales.  
  
 Una palabra clave contextual tiene un significado especial dentro de los contextos de programas concretos.  Dentro del programa general, por ejemplo, `sealed` es tratado como un identificador ordinario.  No obstante, cuando ocurre dentro de la parte de la declaración de un tipo de clase de referencia administrada, se trata como una palabra clave dentro del contexto de esta declaración de clase.  Esto minimiza el posible impacto invasivo de la introducción de una nueva palabra clave en el lenguaje, algo que creemos que es muy importante para los usuarios con una base de código existente.  Al mismo tiempo, permite a los usuarios de la nueva funcionalidad tener una experiencia de gran calidad de la característica de lenguaje adicional, algo que no era posible con Extensiones administradas.  Para obtener un ejemplo de la forma de utilizar `sealed`, vea [Declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md).  
  
 Una palabra clave espaciada, como `value class`, es un caso especial de una palabra clave contextual.  Empareja una palabra clave existente con un modificador de contexto, con un espacio de separación entre ambos.  El par se considera como una única unidad en lugar de como dos palabras clave independientes.  
  
## Vea también  
 [Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)