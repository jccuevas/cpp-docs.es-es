---
title: Crear su propia función auxiliar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6b8e397fecc8f14140cd7c86217421d5aa1a749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="developing-your-own-helper-function"></a>Crear una función auxiliar personalizada
Desea proporcionar su propia versión de la rutina para realizar un procesamiento específico basado en los nombres de las DLL o las importaciones. Hay dos métodos para hacerlo: de codificación sus propias, basándose en el código proporcionado, es posible o simplemente enlazar la versión proporcionada mediante los enlaces de notificación detallados anteriormente.  
  
 Codificar una versión propia  
 Esto es bastante sencillo, ya que puede utilizar básicamente el código proporcionado como guía para el nuevo. Por supuesto, deben cumplir las convenciones de llamada y si vuelve a los thunks generados por el enlazador, debe devolver un puntero a función apropiado. Una vez en el código, puede hacer prácticamente todo lo que desees con el fin de satisfacer la llamada o sacar partido de la llamada.  
  
 Usar el enlace de notificación de procesamiento de inicio  
 Probablemente será más fácil basta con proporcionar un nuevo puntero a una función de enlace de notificación proporcionado por el usuario que recibe los mismos valores que la aplicación auxiliar de forma predeterminada en la notificación dliStartProcessing. En ese momento, la función de enlace puede ser básicamente la nueva función de aplicación auxiliar, como un retorno correcto a la aplicación auxiliar predeterminada omitirá cualquier procesamiento posterior en la aplicación auxiliar de forma predeterminada.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)