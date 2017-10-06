---
title: Compatibilidad con versiones anteriores | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: eb334c84fb0b0eb04b9ef48443beedeece23eb0e
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="backward-compatibility"></a>Compatibilidad con versiones anteriores
Para la compatibilidad entre versiones del producto, la biblioteca /OLDNAMES.LIB asigna nombres anteriores a nuevos nombres. Por ejemplo, `open` se asigna a `_open`. Se debe establecer un vínculo explícito con /OLDNAMES.LIB solo cuando se compila con las siguientes combinaciones de opciones de la línea de comandos:  
  
-   `/Zl` (omitir nombres de biblioteca predeterminados del archivo objeto) y `/Ze` (valor predeterminado: usar extensiones de Microsoft)  
  
-   `/link` (control de enlazador), `/NOD` (valor no predeterminado: búsqueda de biblioteca) y `/Ze`  
  
 Para más información sobre las opciones de la línea de comandos del compilador, vea la [referencia del compilador](../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)
