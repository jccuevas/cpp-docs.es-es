---
title: "Conformidad con ANSI C | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Ansi"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ANSI [C++], estándar de C"
  - "compatibilidad [C++], ANSI C"
  - "conformidad con ANSI C"
  - "convenciones [C++], extensiones para Microsoft"
  - "convenciones de nomenclatura de extensiones de Microsoft"
  - "convenciones de nomenclatura [C++], biblioteca Microsoft"
  - "caracteres de subrayado"
  - "caracteres de subrayado, iniciales"
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Conformidad con ANSI C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La convención de nomenclatura para los identificadores Microsoft\- específicos en el sistema de motor en tiempo de ejecución \(como funciones, macros, constantes, variables, y definiciones de tipo\) es ANSI\- bajo.  En esta documentación, cualquier función en tiempo de ejecución que siga las normas ANSI\/ISO C se anota es compatible con ANSI.  Las aplicaciones de ANSI\- bajo deben utilizar sólo estas funciones compatibles ANSI.  
  
 Los nombres de funciones y variables globales Microsoft\- específicas comienzan con un único carácter de subrayado.  Estos nombres se pueden reemplazar solo localmente, dentro del ámbito de código.  Por ejemplo, cuando se incluye archivos de encabezado en tiempo de ejecución de Microsoft, puede sin embargo localmente reemplazar la función Microsoft\- concreta denominada `_open` declarar una variable local del mismo nombre.  Sin embargo, no puede utilizar este nombre para formar la función o la variable global global.  
  
 Los nombres de macros Microsoft\- específicas y de constantes de manifiesto comienzan con dos caracteres de subrayado, o con un único carácter de subrayado inicial inmediatamente seguido por una letra mayúscula.  El ámbito de estos identificadores es absoluto.  Por ejemplo, no puede utilizar el identificador Microsoft\- concreto **\_UPPER** por este motivo.  
  
## Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)