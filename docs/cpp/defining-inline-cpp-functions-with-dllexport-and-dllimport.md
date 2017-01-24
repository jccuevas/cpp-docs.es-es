---
title: "Definir funciones insertadas de C++ con dllexport y dllimport | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dllexport (atributo) [C++], funciones inline"
  - "dllimport (atributo) [C++], funciones inline"
  - "funciones [C++], definir alineado"
  - "inline (funciones) [C++], definir"
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Definir funciones insertadas de C++ con dllexport y dllimport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Puede definir como alineada una función con el atributo `dllexport`.  En este caso, siempre se crean instancias de la función, y siempre se exporta, independientemente de si un módulo del programa hace referencia o no a la función.  Se supone que otro programa importa la función.  
  
 También puede definir como alineada una función declarada con el atributo **dllimport**.  En este caso, la función se puede expandir \(según las especificaciones de \/Ob\), pero nunca se pueden crear instancias de ella.  En concreto, si se toma la dirección de una función alineada importada, se devuelve la dirección de la función que reside en la DLL.  Este comportamiento es el mismo que cuando se toma la dirección de una función importada no alineada.  
  
 Estas reglas se aplican a las funciones insertadas cuyas definiciones aparecen dentro de una definición de clase.  Además, los datos y cadenas locales estáticos en funciones insertadas mantienen las mismas identidades entre la DLL y el cliente que en un solo programa \(es decir, un archivo ejecutable sin interfaz DLL\).  
  
 Tome precauciones cuando proporcione funciones insertadas importadas.  Por ejemplo, si actualiza la DLL, no suponga que el cliente utilizará la versión modificada de la DLL.  Para asegurarse de que se carga la versión correcta, recompile el cliente de DLL también.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)