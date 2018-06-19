---
title: Hospedar controles ActiveX mediante AXHost de ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5057a077e8e778fa3d943b736d51d19af8f60fc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356258"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hospedar controles ActiveX mediante AXHost de ATL
En este tema se muestra cómo crear AXHost y cómo hospedar un control ActiveX mediante varias funciones ATL. También muestra cómo obtener acceso a los eventos de control y el receptor (mediante [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) desde el control hospedado. El ejemplo hospeda el control de calendario en una ventana principal o en una ventana secundaria.  
  
 Tenga en cuenta la definición de la `USE_METHOD` símbolos. Puede cambiar el valor de este símbolo que oscile entre 1 y 8. El valor del símbolo determina cómo se creará el control:  
  
-   Para los valores impares de `USE_METHOD`, la llamada para crear una ventana de las subclases de host y lo convierte en un host de control. Para los valores impares, el código crea una ventana secundaria que actúa como un host.  
  
-   Para los valores de `USE_METHOD` entre 1 y 4, el acceso al control y la recepción de eventos se llevan a cabo en la llamada que sirve para crear el host. Los valores entre 5 y 8 consultan al host para las interfaces y enlazan el receptor.  
  
 A continuación, se muestra un resumen:  
  
|USE_METHOD|administrador de flujos de trabajo|Controlar el acceso y la recepción de eventos|Función explicada|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Ventana secundaria|Un solo paso|CreateControlLicEx|  
|2|Ventana principal|Un solo paso|AtlAxCreateControlLicEx|  
|3|Ventana secundaria|Un solo paso|CreateControlEx|  
|4|Ventana principal|Un solo paso|AtlAxCreateControlEx|  
|5|Ventana secundaria|Varios pasos|CreateControlLic|  
|6|Ventana principal|Varios pasos|AtlAxCreateControlLic|  
|7|Ventana secundaria|Varios pasos|CreateControl|  
|8|Ventana principal|Varios pasos|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [Clase CAxWindow2T](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic (interfaz)](../atl/reference/iaxwinhostwindowlic-interface.md)

