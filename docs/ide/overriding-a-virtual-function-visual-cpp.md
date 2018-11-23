---
title: Reemplazar una función virtual
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 9bb3fd34bbfa14cce1595ed586c4e1b66518e7b7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694028"
---
# <a name="override-a-virtual-function"></a>Reemplazar una función virtual

Las funciones virtuales definidas en una clase base se pueden reemplazar desde la [ventana Propiedades](/visualstudio/ide/reference/properties-window) de Visual Studio.

**Para reemplazar una función virtual en la ventana Propiedades:**

1. En la Vista de clases, seleccione la clase.

1. En la ventana Propiedades, seleccione el botón **Invalidaciones**.

   > [!NOTE]
   > El botón **Invalidaciones** está disponible cuando se selecciona el nombre de clase en la Vista de clases o al seleccionar en la ventana de código fuente.

   En la columna de la izquierda se enumeran las funciones virtuales. Si el nombre de una función virtual también aparece en la columna de la derecha, ya se ha implementado una invalidación.

1. Si la función no tiene ninguna invalidación, seleccione la celda de la columna derecha de la ventana Propiedades para mostrar el nombre sugerido de la invalidación de función como \<add>*FuncName*.

1. Seleccione el nombre sugerido para agregar código stub para la función.

1. Para modificar una función de invalidación, haga doble clic en el nombre de la función en la Vista de clases y modifique el código en la ventana de código fuente.

Para quitar una invalidación, seleccione el nombre de la función de invalidación en la columna derecha y luego \<delete>*FuncName*. El código de la función se marca como comentario.
