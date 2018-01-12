---
title: Admitir IDispatch y IErrorInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs: C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f39db3e844df884e8e95352bed2a078b01beede8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Admitir IDispatch y IErrorInfo
Puede utilizar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la `IDispatch Interface` parte de las interfaces duales en el objeto.  
  
 Si el objeto utiliza el `IErrorInfo` interfaz para notificar errores que se devuelva al cliente, a continuación, el objeto debe admitir la `ISupportErrorInfo Interface` interfaz. La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si sólo dispone de una única interfaz que genera errores en el objeto.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

