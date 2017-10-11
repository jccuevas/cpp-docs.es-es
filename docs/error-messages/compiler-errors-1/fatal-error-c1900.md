---
title: Error irrecuperable C1900 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3b64061401189fb37f28492fbffe1e9941e8aab8
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1900"></a>Error irrecuperable C1900
Il 'tool1', versión 'number1', no coincide con 'tool2', versión 'number2'  
  
 Las herramientas ejecutadas en varias transferencias del compilador no coinciden. ***number1*** y ***número2*** hacen referencia a las fechas de los archivos. Por ejemplo, en la transferencia 1, el front-end del compilador ejecuta (c1.dll) y, en la transferencia 2, el back-end del compilador ejecuta (c2.dll). Las fechas de los archivos deben coincidir.  
  
 Para corregir este problema, asegúrese de que se han aplicado todas las actualizaciones a Visual Studio. Si el problema persiste, use **programas y características** en el Panel de Control de Windows para reparar o reinstalar Visual Studio.
