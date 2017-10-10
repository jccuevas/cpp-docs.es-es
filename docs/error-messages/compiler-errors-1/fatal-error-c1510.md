---
title: Error irrecuperable C1510 | Documentos de Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: 1
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 373cd74b1649fb9c1bd87cad1903df183f153c0f
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1510"></a>Error irrecuperable C1510
No se puede abrir el archivo clui.dll de recursos de idioma  
  
 El compilador no puede cargar la DLL de recursos de idioma.  
  
Hay dos causas comunes de este problema. Cuando se usa el compilador de 32 bits y herramientas, puede ver este error para los proyectos grandes que utilizan más de 2GB de memoria durante un vínculo. Una posible solución en sistemas de Windows de 64 bits es usar a nativo de 64 bits o entre el compilador y las herramientas para generar el código. Esto aprovecha el mayor espacio de memoria disponible para las aplicaciones de 64 bits. Si debe utilizar un compilador de 32 bits porque se está ejecutando en un sistema de 32 bits, en algunos casos puede aumentar la cantidad de memoria disponible para el vinculador / 3GB. Para obtener más información, consulte [4 gigabytes para la optimización: BCDEdit y Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) y [BCDEdit /Set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) comando.  

La otra causa habitual es una instalación de Visual Studio interrumpida o está incompleta. En este caso, ejecute el programa de instalación para reparar o reinstalar Visual Studio.  
  
