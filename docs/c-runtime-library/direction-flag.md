---
title: "Marca de dirección | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.flags
dev_langs: C++
helpviewer_keywords: direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b26cb08800bf7d2855c7972c63c0bea414d58c99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="direction-flag"></a>Marca de dirección
La marca de dirección es una marca de CPU específica de procesadores Intel 80x86. Se aplica a todas las instrucciones de ensamblado que usan el prefijo REP (repeticiones), como MOVS, MOVSD, MOVSW y otros. Las direcciones proporcionadas para las instrucciones aplicables se incrementan si está desactivada la marca de dirección.  
  
 Las rutinas de tiempo de ejecución de C suponen que la marca de dirección está desactivada. Si usa otras funciones con las funciones de tiempo de ejecución de C, debe asegurarse de que las demás funciones dejan la marca de dirección tal cual o que la restauran a su condición original. Esperar que la marca de dirección se desactive al realizar la entrada hace que el código de tiempo de ejecución resulte más rápido y eficaz.  
  
 Las funciones de la biblioteca en tiempo de ejecución de C, como las rutinas de manipulación de cadenas y de manipulación de búfer, esperan que la marca de dirección se desactive.  
  
## <a name="see-also"></a>Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)