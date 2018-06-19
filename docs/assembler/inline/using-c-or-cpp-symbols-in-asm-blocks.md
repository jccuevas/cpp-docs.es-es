---
title: Usar símbolos de C o C++ en bloques __asm | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746614de653649747bf20ae4c223e5687ee53f5c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049432"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Usar símbolos de C o C++ en bloques __asm
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Un bloque `__asm` puede hacer referencia a cualquier símbolo de C o C++ en el ámbito donde aparece el bloque. (Los símbolos de C y C++ son nombres de variable, nombres de función y etiquetas; es decir, nombres que no sean constantes simbólicas ni miembros de `enum`. No se puede llamar a funciones miembro de C++).  
  
 Se aplican algunas restricciones al uso de los símbolos de C y C++:  
  
-   Cada instrucción del lenguaje de ensamblado solo puede contener un símbolo de C o C++. Pueden aparecer varios símbolos en la misma instrucción de ensamblado solo con **longitud**, **tipo**, y **tamaño** expresiones.  
  
-   Las funciones a las que se hace referencia en un bloque `__asm` se deben declarar antes (mediante prototipo) en el programa. De lo contrario, el compilador no podrá distinguir los nombres de función y las etiquetas en el bloque `__asm`.  
  
-   En un bloque `__asm` no puede haber ningún símbolo de C o C++ escrito igual que las palabras reservadas de MASM (independientemente de si es en mayúsculas o minúsculas). Palabras reservadas de MASM incluyen nombres de instrucciones, como **PUSH** y registrar los nombres, como SI.  
  
-   Las etiquetas de estructura y unión no se reconocen en los bloques `__asm`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)