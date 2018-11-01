---
title: Definir teclas de acceso
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 8682ab38abebe1c453ef562e8eaac0e627f5c4bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488925"
---
# <a name="defining-mnemonics-access-keys"></a>Definir teclas de acceso

Normalmente, los usuarios del teclado mueve el foco de entrada de un control a otro en un cuadro de diálogo con el **ficha** y **flecha** claves. Sin embargo, puede definir una clave de acceso (un nombre mnemotécnico o fácil de recordar) que permite a los usuarios elegir un control presionando una sola clave.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Para definir una tecla de acceso para un control con un título visible (botones de comando, casillas y botones de radio)

1. Seleccione el control en el cuadro de diálogo.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en el **título** propiedad, escriba un nombre nuevo para el control, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso para ese control. Por ejemplo: `&Radio1`.

3. Presione **ENTRAR**.

   Aparece un subrayado en el título mostrado para indicar la clave de acceso, por ejemplo, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Para definir una tecla de acceso para un control sin un título visible

1. Cree un título para el control mediante el uso de un **texto estático** en controlar la [cuadro de herramientas](/visualstudio/ide/reference/toolbox).

2. En el título de texto estático, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso.

3. Asegúrese de que el control de texto estático precede inmediatamente al control correspondiente en el orden de tabulación.

Todas las claves de acceso dentro de un cuadro de diálogo deben ser únicas.

### <a name="to-check-for-duplicate-access-keys"></a>Comprobar teclas de acceso duplicadas

1. En el **formato** menú, haga clic en **Comprobar teclas de acceso**.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)