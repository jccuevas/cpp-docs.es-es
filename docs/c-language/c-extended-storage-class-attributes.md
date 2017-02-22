---
title: "Atributos extendidos de clase de almacenamiento de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C]"
  - "atributos extendidos"
  - "atributos de clase de almacenamiento extendidos"
  - "especificadores de clase de almacenamiento, clases de almacenamiento de C"
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Atributos extendidos de clase de almacenamiento de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Encontrará información más actualizada sobre este tema en [\_\_declspec \(Referencia de C\+\+\)](../cpp/declspec.md).  
  
 La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft para el lenguaje C.  Los atributos de clase de almacenamiento que usan la sintaxis de atributo extendido son thread, naked, dllimport y dllexport.  
  
 La sintaxis de atributo extendido para especificar información de clase de almacenamiento utiliza la palabra clave \_\_declspec, que especifica que una instancia de un tipo determinado se debe almacenar con un atributo de clase de almacenamiento específico de Microsoft \(thread, naked, dllimport o dllexport\).  Algunos ejemplos de otros modificadores de clase de almacenamiento son las palabras clave static y extern.  Sin embargo, estas palabras clave forman parte del estándar ANSI C y, como tales, no se tratan con la sintaxis de atributo extendido.  
  
## Sintaxis  
 *storage\-class\-specifier*:  
 `__declspec` \( *extended\-decl\-modifier\-seq* \) \/\* Específico de Microsoft \*\/  
  
 *extended\-decl\-modifier\-seq*:  
 *extended\-decl\-modifier*  opt  
  
 *extended\-decl\-modifier\-seq extended\-decl\-modifier*  
  
 *extended\-decl\-modifier*:  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
 El espacio en blanco separa los modificadores de la declaración.  Observe que el elemento *extended\-decl\-modifier\-seq* puede estar vacío; en este caso, \_\_declspec no tiene ningún efecto.  
  
 Los atributos de clase de almacenamiento thread, naked, dllimport y dllexport son una propiedad solo de la declaración de los datos o función a los que se aplican; no vuelven a definir los atributos de tipo de la propia función.  El atributo thread afecta solo a los datos.  El atributo naked solo afecta a las funciones.  Los atributos dllimport y dllexport afectan a funciones y datos.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)