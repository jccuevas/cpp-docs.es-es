---
title: Cambiar las propiedades de una cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource identifiers, string properties
- string tables, changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5897801a0b0350d813f7dddc5d1595e04213e2dd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221645"
---
# <a name="changing-the-properties-of-a-string"></a>Cambiar las propiedades de una cadena

### <a name="to-change-a-string-or-its-identifier"></a>Para cambiar una cadena o su identificador.

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Seleccione la cadena que desea editar y haga doble clic en el **ID**, **valor**, o **título** columna. Ahora hacer lo siguiente:

   - Seleccione un **ID** desde el **Id. de lista desplegable** lista o escriba un `ID` directamente en su lugar.

   - Escriba un número diferente de la **valor** columna.

   - Escriba las modificaciones en el **título** columna.

        > [!NOTE]
        >  También puede editar propiedades de una cadena en el [ventana propiedades](/visualstudio/ide/reference/properties-window).

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cadenas](../windows/string-editor.md)  