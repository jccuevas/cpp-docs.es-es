---
title: Nuevo cuadro de diálogo de recurso de barra de herramientas (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
ms.openlocfilehash: 7c45daeb2c07426918f1a636f4230c1c07026ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595928"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>Nuevo cuadro de diálogo de recurso de barra de herramientas (C++)

El **nuevo recurso de barra de herramientas** cuadro de diálogo permite especificar el ancho y alto de los botones que se va a agregar a un recurso de barra de herramientas en un proyecto de C++. El valor predeterminado es 16 x 15 píxeles.

Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por tanto, si establece la **ancho del botón** en 512, solo puede tener cuatro botones. Si establece el ancho en 513, solo puede tener tres botones.

### <a name="button-width"></a>Ancho del botón

Proporciona un espacio para escribir el ancho de los botones de barra de herramientas que se va a convertir de un recurso de mapa de bits en un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).

### <a name="button-height"></a>Alto de botón

Proporciona un espacio para escribir el alto de los botones de barra de herramientas que se va a convertir de un recurso de mapa de bits en un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Propiedades de los botones de la barra de herramientas](../windows/toolbar-button-properties.md)<br/>
[Conversión de mapas de bits en barras de herramientas](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Editor de barras de herramientas](../windows/toolbar-editor.md)