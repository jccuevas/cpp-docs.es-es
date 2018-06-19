---
title: Sugerencias de programación para MBCS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb6e298961580c959235a97f37793df41d1124f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855284"
---
# <a name="mbcs-programming-tips"></a>Sugerencias de programación para MBCS
En el nuevo desarrollo, debe utilizar la codificación de caracteres Unicode para todas las cadenas que los usuarios finales pueden ver posiblemente. MBCS es una tecnología heredada reemplazada por Unicode. En esta sección se proporcionan sugerencias para los desarrolladores que deben mantener programas existentes que utilizan MBCS y donde no es práctico convertir a Unicode. Los consejos se refieren a aplicaciones MFC y aplicaciones creadas sin MFC. Entre los temas se incluyen los siguientes:  
  
-   [Consejos generales sobre la programación con MBCS](../text/general-mbcs-programming-advice.md)  
  
-   [Aumento y disminución de punteros](../text/incrementing-and-decrementing-pointers.md)  
  
-   [Índices de byte](../text/byte-indices.md)  
  
-   [Último carácter de una cadena](../text/last-character-in-a-string.md)  
  
-   [Asignación de caracteres](../text/character-assignment.md)  
  
-   [Comparación de caracteres](../text/character-comparison.md)  
  
-   [Desbordamiento de búfer](../text/buffer-overflow.md)  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con los juegos de caracteres multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)