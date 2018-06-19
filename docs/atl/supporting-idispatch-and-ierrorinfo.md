---
title: Admitir IDispatch y IErrorInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94f4c99da3989cce84bd5b6bd3bbfee8df97ff43
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360954"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Admitir IDispatch y IErrorInfo
Puede utilizar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la `IDispatch Interface` parte de las interfaces duales en el objeto.  
  
 Si el objeto utiliza el `IErrorInfo` interfaz para notificar errores que se devuelva al cliente, a continuación, el objeto debe admitir la `ISupportErrorInfo Interface` interfaz. La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si sólo dispone de una única interfaz que genera errores en el objeto.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

