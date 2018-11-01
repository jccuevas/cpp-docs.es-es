---
title: Admitir IDispatch e IErrorInfo
ms.date: 11/04/2016
f1_keywords:
- IErrorInfo
- IDispatch
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: ea45f0bdd2363f4392baee049629c55259e45af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502441"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Admitir IDispatch e IErrorInfo

Puede usar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la `IDispatch Interface` parte de las interfaces duales en el objeto.

Si el objeto utiliza el `IErrorInfo` interfaz para notificar los errores que se devuelva al cliente, a continuación, el objeto debe admitir la `ISupportErrorInfo Interface` interfaz. La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si solo tiene una única interfaz que genera errores en el objeto.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

