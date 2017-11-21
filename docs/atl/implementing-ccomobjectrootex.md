---
title: Implementar CComObjectRootEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CComObjectRootEx
dev_langs: C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 960f7989d3891be4cf23ef75b0982a2577f5e95e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-ccomobjectrootex"></a>Implementar CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) es fundamental; todos los objetos ATL deben tener una instancia de `CComObjectRootEx` o [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) en su herencia. `CComObjectRootEx` ofrece el mecanismo de `QueryInterface` predeterminado basado en entradas de asignación COM.  
  
 A través de esta asignación COM, las interfaces de un objeto se exponen a un cliente cuando este realiza una consulta sobre una interfaz. La consulta se tramita a través de `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` solo administra interfaces de la tabla de asignación COM.  
  
 Puede especificar interfaces en la tabla de asignación de COM con el [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) macro o una de sus variantes. Por ejemplo, en el siguiente código se especifican las interfaces `IDispatch`, `IBeeper` y `ISupportErrorInfo` en la tabla de asignación COM:  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)   
 [Macros de mapa COM](../atl/reference/com-map-macros.md)

