---
title: Ejemplo de puntos de conexión ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a35b1e40718c26eb094eddb420f885a37907071
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212599"
---
# <a name="atl-connection-point-example"></a>Ejemplo de puntos de conexión ATL
En este ejemplo se muestra un objeto que admite [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) como una interfaz de salida:  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]  
  
 Al especificar `IPropertyNotifySink` como una interfaz de salida, puede usar la clase [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) en lugar de `IConnectionPointImpl`. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]  
  
## <a name="see-also"></a>Vea también  
 [Punto de conexión](../atl/atl-connection-points.md)

