---
title: Consideraciones de inicio adicionales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57b1de8fbbdb3d969dca8e84e57e18b81749d944
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="additional-startup-considerations"></a>Consideraciones de inicio adicionales
En C++, la creación y destrucción de objetos pueden implicar la ejecución de código de usuario. Por lo tanto, es importante entender qué inicializaciones se producen antes de la entrada a **principal** y qué destructores se invocan después de la salida de **principal**. (Para obtener información detallada sobre la construcción y destrucción de objetos, consulte [constructores](../cpp/constructors-cpp.md) y [destructores](../cpp/destructors-cpp.md).)  
  
 Las inicializaciones siguientes tienen lugar antes de que empiece a **principal**:  
  
-   Inicialización predeterminada de datos estáticos en cero. Todos los datos estáticos sin inicializadores explícitos se establecen en cero antes de ejecutar cualquier otro código, incluida la inicialización en tiempo de ejecución. Los miembros de datos estáticos todavía se deben definir explícitamente.  
  
-   Inicialización de objetos estáticos globales en una unidad de traducción. Esto puede darse antes de la entrada a **principal** o antes del primer uso de cualquier función u objeto de unidad de traducción del objeto.  
  
 **Específicos de Microsoft**  
  
 En Microsoft C++, objetos estáticos globales se inicializan antes de la entrada a **principal**.  
  
 **FIN de Específicos de Microsoft**  
  
 Los objetos estáticos globales que son mutuamente interdependientes pero en diferentes unidades de traducción pueden provocar un comportamiento incorrecto.  
  
## <a name="see-also"></a>Vea también  
 [Inicio y finalización](../cpp/startup-and-termination-cpp.md)