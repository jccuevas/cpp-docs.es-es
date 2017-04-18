---
title: Error irrecuperable C1510 | Documentos de Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 05aee6ce5cba18d0517a134eb217a149098beb6e
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1510"></a>Error irrecuperable C1510
No se puede abrir el archivo clui.dll de recursos de idioma  
  
 El compilador no puede cargar la DLL de recursos de idioma.  
  
Hay dos causas comunes de este problema. Cuando se usa el compilador de 32 bits y herramientas, puede ver este error para los proyectos grandes que utilizan más de 2GB de memoria durante un vínculo. Una posible solución en sistemas de Windows de 64 bits es usar a nativo de 64 bits o entre el compilador y las herramientas para generar el código. Esto aprovecha el mayor espacio de memoria disponible para las aplicaciones de 64 bits. Si debe utilizar un compilador de 32 bits porque se está ejecutando en un sistema de 32 bits, en algunos casos puede aumentar la cantidad de memoria disponible para el vinculador / 3GB. Para obtener más información, consulte [4 gigabytes para la optimización: BCDEdit y Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) y [BCDEdit /Set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) comando.  

La otra causa habitual es una instalación de Visual Studio interrumpida o está incompleta. En este caso, ejecute el programa de instalación para reparar o reinstalar Visual Studio.  
  
