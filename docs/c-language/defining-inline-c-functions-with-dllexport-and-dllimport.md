---
title: "Definir funciones insertadas de C con dllexport y dllimport | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "dllexport (atributo) [C++]"
  - "dllexport (atributo) [C++], funciones inline"
  - "dllimport (atributo) [C++], funciones inline"
  - "inline (funciones) [C++], con dllexport y dllimport"
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Definir funciones insertadas de C con dllexport y dllimport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Puede definir como alineada una función con el atributo `dllexport`.  En este caso, siempre se crean instancias de la función, y siempre se exporta, independientemente de si un módulo del programa hace referencia o no a la función.  Se supone que otro programa importa la función.  
  
 También puede definir como alineada una función declarada con el atributo **dllimport**.  En este caso, la función puede expandirse \(de acuerdo con la especificación de opción del compilador \/Ob \(inline\)\), pero no puede crearse una instancia de ella.  En concreto, si se toma la dirección de una función alineada importada, se devuelve la dirección de la función que reside en la DLL.  Este comportamiento es el mismo que cuando se toma la dirección de una función importada no alineada.  
  
 Los datos y cadenas locales estáticos en funciones inline mantienen las mismas identidades entre la DLL y el cliente que mantendrían en un solo programa \(es decir, un archivo ejecutable sin una interfaz DLL\).  
  
 Tome precauciones cuando proporcione funciones insertadas importadas.  Por ejemplo, si actualiza la DLL, no suponga que el cliente utilizará la versión modificada de la DLL.  Para asegurarse de que se carga la versión correcta, recompile el cliente de DLL también.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Funciones de importación y exportación de archivos DLL](../c-language/dll-import-and-export-functions.md)