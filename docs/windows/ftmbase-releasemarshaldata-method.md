---
title: ReleaseMarshalData (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
dev_langs:
- C++
helpviewer_keywords:
- ReleaseMarshalData method
ms.assetid: a94f9940-183a-4fde-8504-d223f346a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2d4bccbcd9f3c3b13fa8be0ccc7afa493751cd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593544"
---
# <a name="ftmbasereleasemarshaldata-method"></a>FtmBase::ReleaseMarshalData (Método)

Destruye un paquete de cálculo de referencias de datos.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*  
Puntero a una secuencia que contiene el paquete de datos que se va a destruir.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[FtmBase (clase)](../windows/ftmbase-class.md)