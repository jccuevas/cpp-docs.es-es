---
title: Colaborar con Live Share para C++ in Visual Studio
description: Use Live Share para C++ en Visual Studio para colaborar en código y compartirlo en tiempo real.
ms.date: 05/24/2019
ms.openlocfilehash: 0ebdd77d0e277778b48cf69024b24841f775d968
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377283"
---
# <a name="collaborate-using-live-share-for-c"></a>Colaboración mediante Live Share para C++

En Visual Studio 2019 y Visual Studio Code, puede usar **Live Share** para colaborar en proyectos de C++ en tiempo real. Con **Live Share**, otra persona puede editar y depurar su código sin tener que instalar el proyecto ni ninguna de sus dependencias. Las modificaciones de los demás se pueden ver a medida que suceden, y cada modificación se etiqueta con el nombre de la persona que la hizo.

![C&#43;&#43; Live Share Editing](../ide/media/live-share-edit-cpp.png "Edición de acciones en vivo en C++")

## <a name="live-share-host-and-guests"></a>Host e invitados de Live Share

En una sesión de Live Share existe un host y uno o más invitados. Tanto el host como los invitados pueden usar Visual Studio o Visual Studio Code. Así, un host de Visual Studio 2019 en Windows puede compartir código con un invitado de Visual Studio Code en Linux.

El host proporciona a los invitados todo lo que necesitan para ser productivos. No es necesario que los invitados tengan el código fuente, el compilador o las dependencias externas, ni tampoco tener los mismos componentes instalados.

El host y los invitados pueden usar estas características de IntelliSense:

- Lista de miembros
- Ayuda de parámetro
- Información rápida
- Depuración/puntos de interrupción
- Buscar todas las referencias
- Ir a definición
- Búsqueda de símbolos (Ctrl+T)
- Resaltado de referencia
- Diagnósticos/errores/subrayados ondulados

![C&#43;&#43; Depuración de recursos compartidos en vivo](../ide/media/live-share-debug-cpp.png "Depuración de recursos compartidos en vivo en C++")

## <a name="start-and-end-a-live-share-session"></a>Iniciar y finalizar una sesión de Live Share

Para iniciar una sesión de Live Share en Visual Studio, haga clic en el botón Compartir en la parte superior derecha o vaya **a** > Sesión de**colaboración**de inicio de archivo . Esto genera un vínculo que se puede compartir con los colaboradores.

![Botón de Compartir en vivo de C&#43;&#43; ](../ide/media/live-share-button-cpp.png "Botón Compartir en vivo")

Para finalizar una sesión, seleccione **Finalizar sesión de colaboración** en el menú desplegable **Compartir**.

![Botón de Compartir en vivo de C&#43;&#43; ](../ide/media/live-share-end-session-cpp.png "Botón Compartir en vivo")

## <a name="for-more-information"></a>Para obtener más información

Para obtener más información sobre **Live Share** en Visual Studio, vea [¿Qué es Visual Studio Live Share?](/visualstudio/liveshare/) Para obtener más información sobre Live Share en Visual Studio Code, vea [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Consulte también

[Escribir y refactorizar código (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navegación en el código de C++ en Visual Studio](navigate-code-cpp.md)</br>
[Lectura y reconocimiento de código C++](read-and-understand-code-cpp.md)</br>
