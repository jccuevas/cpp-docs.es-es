---
title: Macros y C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7af092d31fb4495be47c88aaaf8830cc05db2bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="macros-and-c"></a>Macros y C++
C++ proporciona nuevas capacidades que suplantan, algunas de ellas, a las proporcionadas por el preprocesador de ANSI C. Estas nuevas capacidades mejoran la seguridad de tipos y la previsibilidad del lenguaje:  
  
-   En C++, los objetos declarados como **const** puede usarse en expresiones constantes. Esto permite que los programas declaren constantes que tienen información de tipo y valor, y enumeraciones que se pueden ver simbólicamente con el depurador. El uso de la directiva `#define` de preprocesador para definir constantes no es tan preciso. Se asigna ningún almacenamiento para una **const** objeto a menos que se encuentra una expresión que tome su dirección en el programa.  
  
-   La capacidad de función insertada de C++ suplanta las macros de tipo de función. Las ventajas de utilizar funciones insertadas respecto a macros son:  
  
    -   Seguridad de tipos. Las funciones insertadas están sujetas a la misma comprobación de tipos que las funciones normales. Las macros no tienen seguridad de tipos.  
  
    -   Se corrige el control de argumentos que tienen efectos secundarios. Las funciones insertadas evalúan las expresiones proporcionadas como argumentos antes de escribir el cuerpo de la función. Por lo tanto, no hay posibilidad de que una expresión con efectos secundarios no sea segura.  
  
 Para obtener más información sobre las funciones insertadas, vea [inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md).  
  
 Por compatibilidad con versiones anteriores, todos los servicios de preprocesador que existían en ANSI C y en las especificaciones anteriores de C++ se conservan para Microsoft C++.  
  
## <a name="see-also"></a>Vea también  
 [Macros predefinidas](../preprocessor/predefined-macros.md)   
 [Macros (C/C++)](../preprocessor/macros-c-cpp.md)