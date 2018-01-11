---
title: Macros de comando y Macros de opciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06f5d48395c0395a85c90096bf2dbad8627ac41a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-macros-and-options-macros"></a>Macros de comando y macros de opciones
Las macros de comando están predefinidas para productos de Microsoft. Macros de opciones representan opciones para estos productos y no están definidas de forma predeterminada. Ambos se usan en las reglas de inferencia predefinidas y se pueden usar en bloques de descripción o las reglas de inferencia definidas por el usuario. Pueden volver a definir las macros de comando para representar la parte o la totalidad de una línea de comandos, incluidas las opciones. Macros de opciones generan una cadena nula si ha dejado sin definir.  
  
|Producto de Microsoft|Macros de comando|Definido como|Macros de opciones|  
|-----------------------|-------------------|----------------|-------------------|  
|Macro Assembler|**AL IGUAL QUE**|ml|**AFLAGS**|  
|Compilador básica|**CONTINUIDAD DEL NEGOCIO**|continuidad del negocio|**BFLAGS**|  
|Compilador de C|**CC**|CL|**CFLAGS**|  
|Compilador C++|**CPP**|CL|**CPPFLAGS**|  
|Compilador C++|**CXX**|CL|**CXXFLAGS**|  
|compilador de recursos|**RC**|rc|**RFLAGS**|  
  
## <a name="see-also"></a>Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)