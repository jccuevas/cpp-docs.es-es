---
title: Utilizar IDispEventSimpleImpl (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed21c862d61686e86efd684a6e88795e4b7bbe51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-idispeventsimpleimpl"></a>Utilizar IDispEventSimpleImpl
Cuando se usa `IDispEventSimpleImpl` para controlar los eventos, deberá:  
  
-   Derive la clase de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).  
  
-   Agregue un mapa de receptores de eventos a la clase.  
  
-   Definir [estructuras _ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) estructuras que describen los eventos.  
  
-   Agregar entradas en el mapa de receptor de eventos mediante el [macro SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) macro.  
  
-   Implemente los métodos que está interesado en el control.  
  
-   Aconsejar y desaconsejar el origen del evento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo controlar la **DocumentChange** eventos desencadenados por de Word **aplicación** objeto. Este evento se define como un método en el **ApplicationEvents** dispinterface.  
  
 El ejemplo está tomado del [ejemplo ATLEventHandling](../visual-cpp-samples.md).  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 El ejemplo se utiliza `#import` para generar los archivos de encabezado necesarios desde la biblioteca de tipos de Word. Si desea utilizar este ejemplo con otras versiones de Word, debe especificar el archivo mso dll correcto. Por ejemplo, Office 2000 proporciona mso9.dll y OfficeXP proporciona mso.dll. Este código se ha simplificado de stdafx.h:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 La única información de la biblioteca de tipos que realmente utilizada en este ejemplo es el CLSID de la palabra **aplicación** objeto y el IID de la **ApplicationEvents** interfaz. Esta información solo se usa en tiempo de compilación.  
  
 Aparece el siguiente código en Simple.h. El código relevante se anota mediante comentarios:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 El siguiente código proviene de Simple.cpp.  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)   
 [Ejemplo ATLEventHandling](../visual-cpp-samples.md)

