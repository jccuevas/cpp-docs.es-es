---
title: Propiedades del botón de barra de herramientas (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
ms.openlocfilehash: f20556ac088180ceb1ed979c3e02ffc465b41c7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665379"
---
# <a name="toolbar-button-properties-c"></a>Propiedades del botón de barra de herramientas (C++)

Las propiedades de un botón de barra de herramientas son:

|Property|Descripción|
|--------------|-----------------|
|**ID**|Define el identificador del botón. La lista desplegable proporciona comunes **ID** nombres.|
|**Ancho**|Establece el ancho del botón. se recomienda 16 píxeles.|
|**Alto**|Establece el alto del botón. Tenga en cuenta que el alto de un botón cambia el alto de todos los botones de la barra de herramientas. se recomienda 15 píxeles.|
|**Preguntar**|Define el mensaje que se muestra en la barra de estado. Agregar un nombre y \n agrega una información sobre herramientas a ese botón de barra de herramientas. Para obtener más información, consulte [creación de una información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Ancho** y **alto** se aplican a todos los botones. Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por lo que si se establece el ancho del botón en 512, solo puede tener cuatro botones y si se establece el ancho en 513, solo puede tener tres botones.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Cambio de las propiedades de un botón de la barra de herramientas](../windows/changing-the-properties-of-a-toolbar-button.md)<br/>
[Editor de barras de herramientas](../windows/toolbar-editor.md)