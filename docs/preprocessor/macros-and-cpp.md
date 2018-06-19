---
title: Macros y C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746b04113e4cb49716e0c1fa6dee69a250bded42
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849618"
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