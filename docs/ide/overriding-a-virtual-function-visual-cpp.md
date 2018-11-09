---
title: Reemplazar una función virtual (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 193c84d2b9a0fe50ae84d3e69834feab27342042
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484146"
---
# <a name="overriding-a-virtual-function-visual-c"></a>Reemplazar una función virtual (Visual C++)

Las funciones virtuales definidas en una clase base se pueden reemplazar desde la [ventana Propiedades](/visualstudio/ide/reference/properties-window) de Visual Studio.

### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Para reemplazar una función virtual en la ventana Propiedades

1. En la Vista de clases, haga clic en la clase.

1. En la ventana Propiedades, haga clic en el botón **Invalidaciones**.

   > [!NOTE]
   >  El botón **Invalidaciones** está disponible cuando se selecciona el nombre de clase en la Vista de clases o al hacer clic en la ventana de código fuente.

   En la columna de la izquierda se enumeran las funciones virtuales. Si el nombre de una función virtual también aparece en la columna de la derecha, ya se ha implementado una invalidación.

1. Si la función no tiene ninguna invalidación, haga clic en la celda de la columna de la derecha en la ventana Propiedades para mostrar el nombre sugerido de la función de invalidación como \<add>*NombreFunción*.

1. Haga clic en el nombre sugerido para agregar código auxiliar para la función.

1. Para modificar una función de invalidación, haga doble clic en el nombre de la función en la Vista de clases y modifique el código en la ventana de código fuente.

Para quitar una invalidación, haga clic en el nombre de la función de invalidación en la columna de la derecha y seleccione \<delete>*NombreFunción*. El código de la función se marca como comentario.

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Agregar una clase](../ide/adding-a-class-visual-cpp.md)<br>
[Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)<br>
[Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)