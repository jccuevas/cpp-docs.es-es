---
title: 'Controles ActiveX MFC: Uso páginas de propiedades estándar | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb1f1d9eed313fefc04a14a004af8c35309949bf
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534994"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Controles ActiveX MFC: Usar páginas de propiedades estándar
En este artículo se describe las páginas de propiedades estándar disponibles para los controles ActiveX y cómo usarlas.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).  
  
 Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:  
  
-   [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC proporciona tres páginas de propiedades estándar para su uso con controles ActiveX: `CLSID_CColorPropPage`, `CLSID_CFontPropPage`, y `CLSID_CPicturePropPage`. Estas páginas muestran una interfaz de usuario para el estándar de color, fuente y las propiedades de imagen, respectivamente.  
  
 Para incorporar estas páginas de propiedades en un control, agregue sus identificadores al código que inicializa la matriz del control de los identificadores de página de propiedades. En el ejemplo siguiente, este código, se encuentra en el archivo de implementación (. (CPP), inicializa la matriz que contendrá todas las tres páginas de propiedades estándar y la página de propiedades predeterminada (denominada `CMyPropPage` en este ejemplo):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Tenga en cuenta que el recuento de páginas de propiedades, en la macro BEGIN_PROPPAGEIDS, es 4. Representa el número de páginas de propiedades admitidas por el control ActiveX.  
  
 Una vez realizadas estas modificaciones, recompile el proyecto. Ahora, el control tiene páginas de propiedades de la fuente, imagen y las propiedades de color.  
  
> [!NOTE]
>  Si no se pueden tener acceso a las páginas de propiedades estándar de control, es posible que la DLL de MFC (MFCxx.DLL) no se ha registrado correctamente con el sistema operativo actual. La causa habitual de instalar Visual C++ en un sistema operativo diferente del que se está ejecutando actualmente.  
  
> [!TIP]
>  Si no están visibles las páginas de propiedades estándar (consulte la nota anterior), registrar la DLL ejecutando RegSvr32.exe desde la línea de comandos con el nombre de ruta de acceso completa al archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)

