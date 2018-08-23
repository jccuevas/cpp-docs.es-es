---
title: DisconnectObject (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b467162d2f5cc5b04bc43a6d31019eb08e17e750
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595411"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject (Método)

Forzosamente libera todas las conexiones externas a un objeto. Servidor del objeto llama a la implementación del objeto de este método antes de apagar.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parámetros

*dwReservado*  
Reservado para uso futuro; debe ser cero.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[FtmBase (clase)](../windows/ftmbase-class.md)