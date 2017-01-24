---
title: "Manual de migraciones C++/CLI | Microsoft Docs"
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
  - "C++/CLI versión 2"
  - "C++/CLI versión 2, extensiones administradas"
  - "Extensiones administradas para C++, actualizar la sintaxis"
  - "migración [C++], C++/CLI versión 2"
  - "actualizar aplicaciones de Visual C++, de Extensiones administradas para C++ a sintaxis de Visual C++ 2005"
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Manual de migraciones C++/CLI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ésta es una guía para trasladar los programas de Visual C\+\+ de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  Para obtener un resumen de lista de comprobación de los cambios sintácticos, vea [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/es-es/edbded88-7ef3-4757-bd9d-b8f48ac2aada).  
  
 C\+\+\/CLI amplía el paradigma de programación de componente dinámico al lenguaje estándar ISO\-C\+\+.  El nuevo lenguaje ofrece varias mejoras significativas en las Extensiones administradas.  En esta sección se ofrece una lista de las características del lenguaje de Extensiones administradas para C\+\+ y sus asignaciones con [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], si existen, y se indican los constructores para los que no existe ninguna asignación.  
  
## En esta sección  
 [Esquema de cambios \(C\+\+\/CLI\)](../dotnet/outline-of-changes-cpp-cli.md)  
 Una descripción de alto nivel de consulta rápida, que proporciona una lista de los cambios bajo cinco categorías generales.  
  
 [Palabras clave del lenguaje \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md)  
 Describe los cambios de palabras claves del lenguaje, incluida la eliminación del subrayado doble y la inclusión de palabras clave contextuales y espaciadas.  
  
 [Tipos administrados \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)  
 Explica los cambios sintácticos de la declaración del Sistema de tipos comunes \(CTS\); esto incluye los cambios de la declaración de clases, matrices \(incluida la matriz de parámetros\), enumeraciones, etc.  
  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 Presenta los cambios que afectan a miembros de clase, como propiedades escalares, propiedades de índice, operadores, delegados y eventos.  
  
 [Tipos de valor y su comportamiento \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Se centra en los tipos de valor y en la nueva familia de punteros interiores y anclados.  También trata sobre una serie de cambios semánticos importantes como la inclusión de la conversión boxing implícita, la inmutabilidad de los tipos de valor a los que se ha aplicado una conversión boxing y la eliminación de la compatibilidad de los constructores predeterminados dentro de las clases de valores.  
  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)  
 Detalla cambios semánticos como la compatibilidad con la notación de la conversión de tipos, el comportamiento de los literales de cadena, y cambios semánticos entre ISO\-C\+\+ y C\+\+\/CLI.  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)