---
title: C++ / CLI manual de migraciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5861a4931a1241a213157b94ca189c6b95f0fb6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccli-migration-primer"></a>Manual de migraciones C++/CLI
Se trata de una guía para mover los programas de Visual C++ de extensiones administradas para C++ a Visual C++. Para obtener un resumen de la lista de comprobación de cambios sintácticos, vea [(NOTINBUILD) de extensiones administradas para C++ Syntax Upgrade Checklist](http://msdn.microsoft.com/en-us/edbded88-7ef3-4757-bd9d-b8f48ac2aada).  
  
 C++ / CLI amplía un paradigma de programación de componente dinámico al lenguaje estándar ISO C++. El nuevo lenguaje ofrece una serie de mejoras significativas en las extensiones administradas. Esta sección proporciona una lista enumerada de las extensiones administradas para características del lenguaje C++ y su asignación a Visual C++ donde existe este tipo de asignación y señala los constructores para los que no existe ninguna asignación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Esquema de cambios (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 Un esquema general para una referencia rápida, que proporciona una lista de los cambios en cinco categorías generales.  
  
 [Palabras clave del lenguaje (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)  
 Trata sobre los cambios en las palabras clave del lenguaje, incluida la eliminación del subrayado doble y la introducción de las palabras clave contextuales y espaciadas.  
  
 [Tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md)  
 Busca cambios sintácticos en la declaración de la Common Type System (CTS): Esto incluye los cambios en la declaración de clases, matrices (incluida la matriz de parámetros), enumeraciones y así sucesivamente.  
  
 [Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 Presenta los cambios que implican a los miembros de clase, como propiedades escalares, propiedades del índice, operadores, delegados y eventos.  
  
 [Tipos de valor y su comportamiento (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Se centra en los tipos de valor y la nueva familia de punteros interiores y anclados. También describe una serie de cambios semánticos importantes como la introducción de la conversión boxing implícita, inmutabilidad de los tipos de valor con conversión boxing y la eliminación de la compatibilidad para los constructores predeterminados dentro de las clases de valor.  
  
 [Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 Detalla cambios semánticos como la compatibilidad con la notación de conversión de cadena literal comportamiento y los cambios en la semántica entre ISO C++ y C++ / CLI.  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)