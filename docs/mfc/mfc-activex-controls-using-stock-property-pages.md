---
title: "Controles ActiveX MFC: Usar p&#225;ginas de propiedades est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLSID_CPicturePropPage"
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
  - "CLSID_CPicturePropPage"
  - "páginas de propiedades estándar de color"
  - "fuentes, controles ActiveX"
  - "controles ActiveX en MFC, páginas de propiedades"
  - "páginas de propiedades estándar de imagen"
  - "propiedades estándar, páginas de propiedades estándar"
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Usar p&#225;ginas de propiedades est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan las páginas de propiedades comunes disponibles para los controles ActiveX y cómo utilizarlos.  
  
 Para obtener más información sobre cómo utilizar las páginas de propiedades de un control ActiveX, vea los artículos siguientes:  
  
-   [Controles ActiveX de MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Controles ActiveX de MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC proporciona tres páginas de propiedades comunes para el uso con controles ActiveX: **CLSID\_CColorPropPage**, **CLSID\_CFontPropPage**, y **CLSID\_CPicturePropPage**.  Estas páginas muestran una interfaz de usuario para el color común, la fuente, y las propiedades de imagen, respectivamente.  
  
 Para escribir estas páginas de propiedades de un control, agregue su id. al código que inicializa la matriz de control de id. de la página de propiedades.  En el ejemplo siguiente, este código, ubicado en el archivo de implementación del control \(.CPP\), inicializa la matriz para contener las tres páginas de propiedades comunes y la propiedad predeterminada \(denominada `CMyPropPage` en este ejemplo\):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/CPP/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Observe que el recuento de páginas de propiedades, en la macro de `BEGIN_PROPPAGEIDS` , es 4.  Esto representa el número de páginas de propiedades admitidas por el control ActiveX.  
  
 Una vez creado estas modificaciones, recompile el proyecto.  El control ahora tiene páginas de propiedades para la fuente, la imagen, y las propiedades de los colores.  
  
> [!NOTE]
>  Si las páginas de propiedades de control no se puede tener acceso, puede ser MFC DLL \(MFCxx.DLL\) no se ha registrado correctamente con el sistema operativo actual.  Esto se produce normalmente de instalar Visual C\+\+ en un sistema operativo diferente del que está ejecutándose actualmente.  
  
> [!TIP]
>  Si las páginas comunes de propiedad no son visibles \(vea la nota anterior\), registre la DLL ejecutando RegSvr32.exe desde la línea de comandos con la ruta de acceso completa al archivo DLL.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)