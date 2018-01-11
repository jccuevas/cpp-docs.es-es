---
title: "Controles de ActiveX MFC: Utilizar páginas de propiedades estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed2d8cd6c852a15c4190c16c049e29577b754ce7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Controles ActiveX MFC: Usar páginas de propiedades estándar
En este artículo se describe las páginas de propiedades estándar disponibles para controles ActiveX y cómo utilizarlas.  
  
 Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:  
  
-   [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC proporciona tres páginas de propiedades estándar para su uso con controles ActiveX: **CLSID_CColorPropPage**, **CLSID_CFontPropPage**, y **CLSID_CPicturePropPage**. Estas páginas muestran una interfaz de usuario estándar de color, fuente y las propiedades de imagen, respectivamente.  
  
 Para incorporar estas páginas de propiedades en un control, agregue sus identificadores al código que inicialice la matriz del control de Id. de página de propiedades. En el ejemplo siguiente, este código, se encuentran en el archivo de implementación (. (CPP), inicializa la matriz para que contenga las tres páginas de propiedades estándar y la página de propiedades predeterminada (denominada `CMyPropPage` en este ejemplo):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Tenga en cuenta que el recuento de propiedad páginas, en el `BEGIN_PROPPAGEIDS` macro, es 4. Esto representa el número de páginas de propiedades admitidas por el control ActiveX.  
  
 Después de realizar estas modificaciones, vuelva a generar el proyecto. Ahora, el control tiene páginas de propiedades de la fuente, imagen y propiedades de color.  
  
> [!NOTE]
>  Si no se pueden tener acceso a las páginas de propiedades estándar de control, puede deberse a que la DLL de MFC (MFCxx.DLL) no se ha registrado correctamente con el sistema operativo actual. Esto suele deberse a la instalación de Visual C++ en un sistema operativo diferente a la que se está ejecutando actualmente.  
  
> [!TIP]
>  Si las páginas de propiedades estándar no son visibles (vea la nota anterior), registre la DLL ejecutando RegSvr32.exe desde la línea de comandos con el nombre de ruta de acceso completa al archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)

