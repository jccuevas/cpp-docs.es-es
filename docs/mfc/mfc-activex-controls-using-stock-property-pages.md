---
title: 'Controles ActiveX MFC: Usar páginas de propiedades estándar'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358187"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Controles ActiveX MFC: Usar páginas de propiedades estándar

En este artículo se describen las páginas de propiedades de stock disponibles para los controles ActiveX y cómo usarlas.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, consulte los artículos siguientes:

- [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)

- [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC proporciona tres páginas de propiedades `CLSID_CColorPropPage`de `CLSID_CFontPropPage`stock `CLSID_CPicturePropPage`para su uso con controles ActiveX: , , y . Estas páginas muestran una interfaz de usuario para las propiedades de color, fuente e imagen de stock, respectivamente.

Para incorporar estas páginas de propiedades en un control, agregue sus ID al código que inicializa la matriz de ida de página de propiedades del control. En el ejemplo siguiente, este código, ubicado en el archivo de implementación del control (. CPP), inicializa la matriz para que contenga las tres páginas de propiedades de stock y la página de propiedades predeterminada (denominada `CMyPropPage` en este ejemplo):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Tenga en cuenta que el recuento de páginas de propiedades, en la macro BEGIN_PROPPAGEIDS, es 4. Esto representa el número de páginas de propiedades admitidas por el control ActiveX.

Una vez realizadas estas modificaciones, vuelva a generar el proyecto. El control ahora tiene páginas de propiedades para las propiedades de fuente, imagen y color.

> [!NOTE]
> Si no se puede tener acceso a las páginas de propiedades de stock de control, puede deberse a que el archivo DLL de MFC (MFCxx.DLL) no se ha registrado correctamente con el sistema operativo actual. Esto suele ser el resultado de la instalación de Visual C++ en un sistema operativo diferente al que se está ejecutando actualmente.

> [!TIP]
> Si las páginas de propiedades de stock no están visibles (consulte la nota anterior), registre el archivo DLL ejecutando RegSvr32.exe desde la línea de comandos con el nombre completo de la ruta de acceso al archivo DLL.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)
