---
title: Error irrecuperable C1900 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7cdd5601785f43748ec87d3219f43728536855
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228992"
---
# <a name="fatal-error-c1900"></a>Error irrecuperable C1900
Il 'tool1', versión 'number1', no coincide con 'tool2', versión 'number2'  
  
 Las herramientas ejecutadas en varias transferencias del compilador no coinciden. ***number1*** y ***número2*** hacen referencia a las fechas de los archivos. Por ejemplo, en la transferencia 1, el front-end del compilador ejecuta (c1.dll) y, en la transferencia 2, el back-end del compilador ejecuta (c2.dll). Las fechas de los archivos deben coincidir.  
  
 Para corregir este problema, asegúrese de que se han aplicado todas las actualizaciones a Visual Studio. Si el problema persiste, use **programas y características** en el Panel de Control de Windows para reparar o reinstalar Visual Studio.