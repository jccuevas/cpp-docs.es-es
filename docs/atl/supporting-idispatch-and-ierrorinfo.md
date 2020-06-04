---
title: Admitir IDispatch e IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 2dcebd215ff5e1bdf72323323dfbaebd16fa3403
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342022"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Admitir IDispatch e IErrorInfo

Puede usar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la `IDispatch Interface` parte de las interfaces duales en el objeto.

Si el objeto utiliza el `IErrorInfo` interfaz para notificar los errores que se devuelva al cliente, a continuación, el objeto debe admitir la `ISupportErrorInfo Interface` interfaz. La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si solo tiene una única interfaz que genera errores en el objeto.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)
