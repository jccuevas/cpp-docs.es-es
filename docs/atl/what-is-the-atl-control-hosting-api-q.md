---
title: "¿Qué es la biblioteca ATL API de hospedaje de controles? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f04f5caa30ab860634f0f96ae18e9da03577ba2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-the-atl-control-hosting-api"></a>¿Qué es la biblioteca ATL API de hospedaje de controles?
Hospedaje de controles de ATL la API es el conjunto de funciones que permite que cualquier ventana pueda actuar como un contenedor de controles ActiveX. Estas funciones pueden ser estática o dinámicamente vinculan en el proyecto, ya que están disponibles como código fuente y exponen por ATL90.dll. Las funciones de hospedaje de controles se muestran en la tabla siguiente.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crea un objeto de host, se conecta a la ventana suministrada y asocia un control existente.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crea un objeto de host, se conecta a la ventana suministrada y a continuación carga un control.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, tal como [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crea un objeto host, se conecta a la ventana suministrada y, a continuación, cargue un control (también permite que los receptores de eventos para configurarse).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, tal como [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crea un cuadro de diálogo no modal a partir de un recurso de cuadro de diálogo y devuelve el identificador de ventana.|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de un recurso de cuadro de diálogo.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Devuelve el **IUnknown** puntero de interfaz del control hospedado en una ventana.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgethost)|Devuelve el **IUnknown** puntero de interfaz del objeto host conectado a una ventana.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializa el código de hospedaje de controles.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Desinicializa el código de hospedaje de controles.|  
  
 El `HWND` parámetros en las tres primeras funciones deben ser una ventana existente de (casi) cualquier tipo. Si se llama a cualquiera de estas tres funciones explícitamente (normalmente, no necesita), no pase un identificador a una ventana que ya está actuando como un host (si lo hace, el objeto de host existente no se liberará).  
  
 Las primeras siete funciones llaman a [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implícitamente.  
  
> [!NOTE]
>  La API de hospedaje de controles constituye la base del soporte de ATL para contención de controles ActiveX. Sin embargo, normalmente hay poca necesidad de llamar directamente a estas funciones si aprovechar o realizar un uso completo de las clases contenedoras de ATL. Para obtener más información, consulte [que ATL clases facilitan la contención de controles ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](which-atl-classes-facilitate-activex-control-containment-q.md)
