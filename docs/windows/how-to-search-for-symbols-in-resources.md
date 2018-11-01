---
title: 'Cómo: buscar símbolos en recursos (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
ms.openlocfilehash: b289fa1c2e5e5e1997c5024b21cae3d7a22b2b8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655996"
---
# <a name="how-to-search-for-symbols-in-resources-c"></a>Cómo: buscar símbolos en recursos (C++)

### <a name="to-find-symbols-in-resources"></a>Para buscar símbolos en recursos:

1. Desde el **editar** menú, elija **Buscar símbolo**.

2. En el [cuadro de diálogo Buscar símbolo](/visualstudio/ide/go-to), en el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba la tecla de aceleración que desea buscar (por ejemplo, ID_ACCEL1).

   > [!TIP]
   > Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) para la búsqueda, debe usar el [comando Buscar en archivos](/visualstudio/ide/reference/find-command) desde el **editar** menú en lugar de la **Buscar símbolo**comando. Para habilitar las expresiones regulares, debe tener la **uso: las expresiones regulares** casilla seleccionada en el [cuadro de diálogo Buscar](/visualstudio/ide/finding-and-replacing-text). Puede hacer clic en el botón de flecha derecha situada a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro.

3. Seleccione cualquiera de los **buscar** opciones.

4. Haga clic en **Buscar siguiente**.

   > [!NOTE]
   > No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar recursos de cadenas a las propiedades.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)