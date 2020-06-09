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
ms.openlocfilehash: 18e482ca93166246df7569be9babff93d983dfd5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618061"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Controles ActiveX MFC: Usar páginas de propiedades estándar

En este artículo se describen las páginas de propiedades estándar disponibles para los controles ActiveX y cómo usarlas.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:

- [Controles ActiveX MFC: Páginas de propiedades](mfc-activex-controls-property-pages.md)

- [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](mfc-activex-controls-adding-another-custom-property-page.md)

MFC proporciona tres páginas de propiedades estándar para su uso con controles ActiveX: `CLSID_CColorPropPage` , `CLSID_CFontPropPage` y `CLSID_CPicturePropPage` . Estas páginas muestran una interfaz de usuario para las propiedades de color, fuente e imagen de las acciones, respectivamente.

Para incorporar estas páginas de propiedades en un control, agregue sus identificadores al código que inicializa la matriz de identificadores de página de propiedades del control. En el ejemplo siguiente, este código, ubicado en el archivo de implementación del control (. CPP), inicializa la matriz para que contenga las tres páginas de propiedades estándar y la página de propiedades predeterminada (denominada `CMyPropPage` en este ejemplo):

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Tenga en cuenta que el recuento de páginas de propiedades, en la macro BEGIN_PROPPAGEIDS, es 4. Representa el número de páginas de propiedades admitidas por el control ActiveX.

Una vez realizadas estas modificaciones, vuelva a compilar el proyecto. El control ahora tiene páginas de propiedades para las propiedades Font, Picture y color.

> [!NOTE]
> Si no se puede tener acceso a las páginas de propiedades estándar del control, puede deberse a que el archivo DLL de MFC (MFCxx. DLL) no se ha registrado correctamente con el sistema operativo actual. Esto suele ser el resultado de la instalación de Visual C++ en un sistema operativo diferente del que se está ejecutando actualmente.

> [!TIP]
> Si las páginas de propiedades estándar no están visibles (vea la nota anterior), registre la DLL ejecutando RegSvr32. exe desde la línea de comandos con el nombre de la ruta de acceso completa al archivo DLL.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Agregar propiedades estándar](mfc-activex-controls-adding-stock-properties.md)
