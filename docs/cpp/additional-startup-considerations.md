---
title: "Consideraciones de inicio adicionales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inicializar antes de principal"
  - "inicio de programa [C++]"
  - "código de inicio"
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Consideraciones de inicio adicionales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En C\+\+, la creación y destrucción de objetos pueden implicar la ejecución de código de usuario.  Por tanto, es importante entender qué inicializaciones se producen antes de la entrada a **main** y qué destructores se invocan después de la salida de **main**. \(Para obtener información detallada sobre la creación y destrucción de objetos, vea [Constructores](../cpp/constructors-cpp.md) y [Destructores](../cpp/destructors-cpp.md)\).  
  
 Las inicializaciones siguientes tienen lugar antes de la entrada a **main**:  
  
-   Inicialización predeterminada de datos estáticos en cero.  Todos los datos estáticos sin inicializadores explícitos se establecen en cero antes de ejecutar cualquier otro código, incluida la inicialización en tiempo de ejecución.  Los miembros de datos estáticos todavía se deben definir explícitamente.  
  
-   Inicialización de objetos estáticos globales en una unidad de traducción.  Esto puede darse antes de la entrada a **main** o antes de que se use por primera vez cualquier función u objeto en la unidad de traducción del objeto.  
  
 **Específicos de Microsoft**  
  
 En Microsoft C\+\+, los objetos estáticos globales se inicializan antes de la entrada a **main**.  
  
 **FIN de Específicos de Microsoft**  
  
 Los objetos estáticos globales que son mutuamente interdependientes pero en diferentes unidades de traducción pueden provocar un comportamiento incorrecto.  
  
## Vea también  
 [Inicio y finalización](../cpp/startup-and-termination-cpp.md)