---
title: "Sugerencias de programación para MBCS | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dc9c5dfd0dafe96e2d37b789b64c8215aa454e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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