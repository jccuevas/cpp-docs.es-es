---
title: Admitir IDispatch e IErrorInfo | Microsoft Docs
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
ms.openlocfilehash: 0d9c27dfe81c3bbd2978f418c8e942ac20190b30
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753613"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Admitir IDispatch e IErrorInfo

Puede usar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la `IDispatch Interface` parte de las interfaces duales en el objeto.

Si el objeto utiliza el `IErrorInfo` interfaz para notificar los errores que se devuelva al cliente, a continuación, el objeto debe admitir la `ISupportErrorInfo Interface` interfaz. La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si solo tiene una única interfaz que genera errores en el objeto.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

