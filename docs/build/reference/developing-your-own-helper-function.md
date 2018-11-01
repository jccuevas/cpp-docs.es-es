---
title: Crear una función del asistente personalizada
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 0bd0066cee875408056bd88895b0b5f449802c5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492019"
---
# <a name="developing-your-own-helper-function"></a>Crear una función del asistente personalizada

Desea proporcionar su propia versión de la rutina para realizar el procesamiento específico en función de los nombres de las DLL o las importaciones. Hay dos métodos para hacerlo: de codificación sus propias, basándose en el código proporcionado, es posible o simplemente enlazar la versión proporcionada mediante los enlaces de notificación detallados anteriormente.

## <a name="code-your-own"></a>Código de su propia

Esto es bastante sencillo, ya que básicamente puede usar el código proporcionado como guía para el nuevo. Por supuesto, deben cumplir las convenciones de llamada y si vuelve a los fragmentos de código thunk generado por el vinculador, debe devolver un puntero a función adecuado. Una vez en el código, puede hacer prácticamente todo lo que quiera con el fin de satisfacer la llamada o sacar partido de la llamada.

## <a name="use-the-start-processing-notification-hook"></a>Use el inicio de procesamiento de enlace de notificación

Probablemente será más fácil simplemente proporcionar un nuevo puntero a una función de enlace de notificación proporcionada por el usuario que recibe los mismos valores que la aplicación auxiliar de forma predeterminada en la notificación dliStartProcessing. En ese momento, la función de enlace básicamente puede convertirse en la nueva función auxiliar, como una devolución correcta a la aplicación auxiliar predeterminada omitirá cualquier procesamiento posterior en la aplicación auxiliar de forma predeterminada.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)